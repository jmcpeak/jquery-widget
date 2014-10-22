# jquery-widget

Have you written a jQuery Widget?

This Angular directive was written as a wrapper to host any Widget written to the specs of the
[Widget Factory](http://api.jqueryui.com/jquery.widget/)

- [demo](http://jsfiddle.net/jmcpeak/scbu1w9f/)
- [multiple widgets](http://jsfiddle.net/jmcpeak/c55rqzcq/)

Check [examples](https://github.com/jmcpeak/jquery-widget/blob/master/app/index.html).

## Features

- Should work with any jQuery Widget written to the jQuery Widget Factory Pattern
- Written as a single general purpose directive - jqueryWidget.js
- just need to write and pass in a config factory object

## Settings in the config factory

        The only thing required to use the directive is the config attribute.
        This is a factory object with all the settings unique to this widget.
        You will define the name of the widget, the events and any options you
        want to use as attributes here
        <div jquery-widget config="sliderConfig" ng-model="model.slider"></div>
     
        register a slider module
        var app = angular.module('slider', ['jqueryWidget']);
        
        register a factory against that module
        app.factory('sliderConfig', function () {
        
        // the name of the widget - $('.selector').slider()
        // required
        this.widget = 'slider';
        
        // the default widget option
        // optional
        // will map to the model based on this
        this.default = 'value';

        // the list of html attributes you want to make available
        // optional 
        this.attributes = ['animate', 'disabled', 'max', 'min', 'orientation', 'range', 'step', 'value', 'values'];

        // Any options you want to set on initialization
        // optional
        this.options = { min: 0, max: 10, step: 1 };
        
        // Where you wire up the jQuery events that are raised
        // optional
        this.events = {
            change: function (event, ui) {
                $log.info('Event: change', event, ui);
            },
            slide: function (event, ui) {
                $log.info('Event: slide', event, ui);
            }
        };

        // An array of events that will get bound
        // optional
        // In this example, whenever the slide event is raised it will be bound to the model - here is where you specify
        // that on the slide event you want ui.value used as the model value 
        // http://api.jqueryui.com/slider/#event-slide
        this.binds = [
            { slide: 'value' }
        ];
        
        // the render callback
        // optional
        // if you need to change some values before they are put back into the widget - for instance the slider step
        // can't be less than 1 or empty - do that here
        this.render = function(viewValue, ngModel) {};


## Browser compatibility

TBD

## Installation using [Bower](http://bower.io/)

- `bower install jquery-widget`

## FAQ

TBD

