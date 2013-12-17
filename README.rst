angular-will-paginate
~~~~~~~~~~~~~~~~~~~~~~~

This is a work in progress directive, mostly a sketch to get willPaginate,
Bootstrap and AngularJS to play nicely together.

This directive allows you to pass in a JSON representation of a will_paginate
collection a callback method and an optional config object and paginate that
collection with AngularJS. Consider this example:

Be sure to inject the willPaginate module in your application definition. Once
included the directive will be available. What follows is a simple example:

.. code-block:: javascript

  angular.module('angularApp', ['willPaginate'])
  .controller('MyCtrl', ['$scope', function($scope) {

      /*
        This is a sample collection but would typically be returned from a resource.
        NOTE: I am using camelcase instead of underscores for all the will_paginate
        variables (e.g. currentPage instead of current_page ).
      */
      $scope.willPaginateCollection = {
        currentPage : 1,
        perPage : 10,
        totalEntries : 50,
        totalPages : 5,
        offset : 0
      };

      /*
        Adding a config object lets you override some of the defaults used
        within the directive. This is totally optional.
      */
      $scope.willPaginateConfig = {
        previousLabel: 'Past',
        nextLabel: 'Future'
      };

      /*
        You must specify a callback function to handle click events from the
        paginator.
      */
      $scope.getPage = function(page){
        console.log(page);
      };
  ]);

Your HTML would look something like this:
.. code-block:: html

    .willPaginate(data-params="willPaginateCollection" data-on-click="getPage" data-config="willPaginateConfig")