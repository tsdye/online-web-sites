+++
title = "Technical Description"
author = ["Thomas S. Dye"]
lastmod = 2018-06-10T08:43:26-10:00
draft = false
weight = 160
+++

### External Symbols {#external-symbols}


#### External Functions {#external-functions}

---

<a id="orga3a2fe8"></a>
<a id="org33bad3a"></a>

-    External Function: `array-fas`     :function:

    -    Syntax

        ```lisp
        (array-fas graph &optional (verbose t))
        ```

    -    Description

        Estimate the feedback arc set of GRAPH using the method of Eades et al. 1993.

        ---

        <a id="org2c44d72"></a>
        <a id="org1a56f80"></a>

-    External Function: `read-configuration-from-files`     :function:

    -    Syntax

        ```lisp
        (read-configuration-from-files verbose &rest file-names)
        ```

    -    Arguments

        verbose
        : Boolean.

        file-names
        : One or more strings or pathnames.

    -    Returns

        A configuration.

    -    Description

        Reads the initialization files FILE-NAMES and returns a configuration. Errors
        out if one or more initialization files were not read. If VERBOSE is non-nil,
        prints a status message.

    -    Example

        ```lisp
        (read-configuration-from-files t "my-config.ini")
        ```

        ---

        <a id="org48451db"></a>
        <a id="org9da1d1d"></a>

-    External Function: `reset-option`     :function:

    -    Syntax

        ```lisp
        (reset-option seq section-name option-name value)
        ```

    -    Arguments

        seq
        : An archaeological sequence.

        section-name
        : A string.

        option-name
        : A string.

        value
        : A string.

    -    Returns

        Nothing.  Called for its side-effects.

    -    Description

        Assign a value, VALUE, to the option, OPTION-NAME, in configurations section,
        SECTION-NAME, in the configuration associated with the archaeological sequence,
        SEQ. Ensures section and option names are not inadvertently created when resetting
        an option.

    -    Example

        ```lisp
        (reset-option *my-sequence* "General configuration" "chronology-graph-draw" "no")
        ```

        ---

        <a id="org3b5529b"></a>
        <a id="org0231a8e"></a>

-    External Function: `run-project`     :function:

    -    Syntax

        ```lisp
        (run-project cfg-file &key (verbose t) (sequence-display png)
                     (chronology-display png) (sequence-cmd xdg-open)
                     (chronology-cmd xdg-open) (draw-sequence t) (draw-chronology t)
                     (delete-sequence nil) (delete-chronology nil))
        ```

    -    Arguments

        cfg-file
        : A string or pathname.

        verbose
        : Boolean.

        sequence-display
        : A string indicating a Graphviz `dot` output file format.

        chronology-display
        : A string indicating a Graphviz `dot` output file format.

        sequence-cmd
        : A string naming the application used to open the sequence graph.

        chronology-cmd
        : A string naming the application used to open the chronology graph.

        draw-sequence
        : Boolean.

        draw-chronology
        : Boolean.

        delete-sequence
        : Boolean.  Delete the sequence graph file after it is displayed.

        delete-chronology
        : Boolean. Delete the chronology graph file after it is displayed.

    -    Returns

        An archaeological sequence.

    -    Description

        Run the project specified in the user's configuration file, CFG-FILE. If
        DRAW-SEQUENCE is non-nil, then create a sequence graph in the format indicated
        by SEQUENCE-DISPLAY and open the graphics file with the shell command,
        SEQUENCE-CMD. If DELETE-SEQUENCE is non-nil, then delete the graphics file after
        it is displayed. If DRAW-CHRONOLOGY is non-nil, then create a sequence graph in
        the format indicated by CHRONOLOGY-DISPLAY and open the graphics file with the
        shell command, CHRONOLOGY-CMD. If DELETE-CHRONOLOGY is non-nil, then delete the
        graphics file after it is displayed. If VERBOSE is non-nil, then advertise
        progress.

    -    Example

        ```lisp
        (run-project "my-config.ini" :verbose nil :sequence-cmd "evince")
        ```

        ---

        <a id="org07c9d3b"></a>
        <a id="org14dfe42"></a>

-    External Function: `run-project/example`     :function:

    -    Syntax

        ```lisp
        (run-project/example example &key (verbose t) (sequence-display png)
                             (chronology-display png) (sequence-cmd xdg-open)
                             (chronology-cmd xdg-open) (draw-sequence t)
                             (draw-chronology t) (delete-sequence t)
                             (delete-chronology t))
        ```

    -    Arguments

        example
        : A keyword, one of :catal-hoyuk, :catal-hoyuk-levels, :catal-hoyuk-distance, :roskams-h, :roskams-h-solarized-light, :roskams-h-solarized-dark, :roskams-jumps, :complex-h-structure, :complex-h-structure-reachable, :fig-12, :fig-12-correlations, :fig-12-periods.

        verbose
        : Boolean.

        sequence-display
        : A string indicating a Graphviz `dot` output file format.

        chronology-display
        : A string indicating a Graphviz `dot` output file format.

        sequence-cmd
        : A string naming the application used to open the sequence graph.

        chronology-cmd
        : A string naming the application used to open the chronology graph.

        draw-sequence
        : Boolean.

        draw-chronology
        : Boolean.

        delete-sequence
        : Boolean.  Delete the sequence graph file after it is displayed.

        delete-chronology
        : Boolean. Delete the chronology graph file after it is displayed.

    -    Returns

        An archaeological sequence.

    -    Description

        Given a keyword, EXAMPLE, that indicates one of the example projects defined
        for the `hm` package, run the project described by the appropriate `.ini` file.

    -    Example

        ```lisp
        (run-project/example :roskams-h :delete-sequence nil)
        ```

        ---

        <a id="orgd500612"></a>
        <a id="orga00af8c"></a>

-    External Function: `set-input-file`     :function:

    -    Syntax

        ```lisp
        (set-input-file seq option file-name header)
        ```

    -    Arguments

        seq
        : An archaeological sequence.

        option
        : A string.

        file-name
        : A string or pathname.

        header
        : Boolean

    -    Returns

        Nothing.  Called for its side-effects.

    -    Description

         If OPTION is recognized, then FILE-NAME and HEADER are registered with the
        configuration associated with the archaeological sequence, SEQ. HEADER is
        interpreted as a boolean.

    -    Example

        ```lisp
        (set-input-file "contexts" "roskams-h-contexts.ini" t)
        ```

        ---

        <a id="orgb2fca99"></a>
        <a id="orgc3b3ee8"></a>

-    External Function: `set-output-file`     :function:

    -    Syntax

        ```lisp
        (set-output-file seq option file-name &optional (verbose t))
        ```

    -    Arguments

        seq
        : An archaeological sequence.

        option
        : A string.

        file-name
        : A string or pathname.

        verbose
        : Boolean.

    -    Returns

        Nothing.  Called for its side-effects.

    -    Description

          Registers the output file, FILE-NAME, with the OPTION in the
        configuration associated with the archaeological sequence, SEQ. Checks if OPTION
        is known and errors out if not. If FILE-NAME exists and VERBOSE is non-nil, then asks
        about overwriting it.

    -    Example

        ```lisp
        (set-output-file *my-seq* "observations" "my-observations.csv")
        ```

        ---

        <a id="org3e4db6d"></a>
        <a id="org86c2050"></a>

-    External Function: `show-classifiable-attributes`     :function:

    -    Syntax

        ```lisp
        (show-classifiable-attributes)
        ```

    -    Arguments

        None.

    -    Returns

        Nothing.  Called for its side-effects.

    -    Description

        Write a list of classifiable attributes to standard output.

    -    Example

        ```lisp
        (show-classifiable-attributes)
        ```

        ---

        <a id="org38c9449"></a>
        <a id="org533d17f"></a>

-    External Function: `show-classifiers`     :function:

    -    Syntax

        ```lisp
        (show-classifiers)
        ```

    -    Arguments

        None.

    -    Returns

        Nothing.  Called for its side effects.

    -    Description

        Write a list of classifiers to standard output.

    -    Example

        ```lisp
        (show-classifiers)
        ```

        ---

        <a id="org0588dff"></a>
        <a id="org2fba9e2"></a>

-    External Function: `show-configuration-options`     :function:

    -    Syntax

        ```lisp
        (show-configuration-options seq section)
        ```

    -    Arguments

        seq
        : An archaeological sequence.

        section
        : A string.

    -    Returns

        A list of strings.

    -    Description

        Print the options in section SECTION of configuration associated with
        the archaeological sequence, SEQ. Errors out if the configuration is not valid or
        SECTION isn't found in the configuration.

    -    Example

        ```lisp
        (show-configuration-options *my-sequence* "General configuration")
        ```

        ---

        <a id="org213e10a"></a>
        <a id="orga9f6a57"></a>

-    External Function: `show-configuration-sections`     :function:

    -    Syntax

        ```lisp
        (show-configuration-sections seq &optional (sort t))
        ```

    -    Arguments

        seq
        : An archaeological sequence.

        sort
        : Boolean.

    -    Returns

        A list of strings.

    -    Description

        Print out the sections in the configuration associated with the
        archaeological sequence, SE, by default in sorted order. If SORT is nil, then
        print out the unsorted section list. Errors out if the configuration associated
        with SEQ is not valid.

    -    Example

        ```lisp
        (show-configuration-sections *my-sequence* nil)
        ```

        ---

        <a id="org7a2f90b"></a>
        <a id="orgef7ea19"></a>

-    External Function: `show-map`     :function:

    -    Syntax

        ```lisp
        (show-map attribute)
        ```

    -    Arguments

        A keyword, ATTRIBUTE, one of :edge-style, :node-style, :node-shape, or :arrow-shape.

    -    Returns

        Nothing.  Called for its side-effects

    -    Description

        Write a lookup map of attributes to standard output.  Raise an error if ATTRIBUTES is out of range.

    -    Example

        ```lisp
        (show-map :edge-style)
        ```

        ---

        <a id="org75c868e"></a>
        <a id="org3c8e2b5"></a>

-    External Function: `write-classifier`     :function:

    -    Syntax

        ```lisp
        (write-classifier classifier-type seq &optional (verbose t))
        ```

    -    Arguments

        classifier-type
        : A keyword.

        seq
        : An archaeological sequence.

        verbose
        : Boolean.

    -    Returns

        Nothing.  Called for its side-effects.

    -    Description

        Write the classifier, CLASSIFIER-TYPE, to a file specified in the user's
        configuration stored in the archaeological sequence, SEQ. If verbose, indicate
        that a file was written.

    -    Example

        ```lisp
        (write-classifier :levels *my-sequence* nil)
        ```

        ---

        <a id="orge341c33"></a>
        <a id="org756bc34"></a>

-    External Function: `write-configuration`     :function:

    -    Syntax

        ```lisp
        (write-configuration seq file-name)
        ```

    -    Arguments

        seq
        : An archaeological sequence.

        file-name
        : A string or pathname.

    -    Returns

        Nothing.  Called for its side-effects.

    -    Description

        Write configuration associated with the archaeological sequence, SEQ, to the
        file, FILE-NAME, in the project directory associated with SEQ.

    -    Example

        ```lisp
        (write-configuration *my-sequence* "my-config.ini")
        ```

        ---

        <a id="org1791a5a"></a>
        <a id="org350ed9e"></a>

-    External Function: `write-default-configuration`     :function:

    -    Syntax

        ```lisp
        (write-default-configuration file-name)
        ```

    -    Argument

        file-name
        : A string or pathname.

    -    Returns

        Nothing.  Called for its side-effects.

    -    Description

        Write the default configuration to the file, FILE-NAME.  Returns an error if
         the directory part of FILE-NAME cannot be found.

    -    Example

        ```lisp
        (write-default-configuration <path/to/default-config.ini>)
        ```


### Index {#index}

[A](#org5833b1d)  [R](#org969f355)  [S](#org0b6ee28)  [W](#org538fc7d)


#### A {#a}

<a id="org5833b1d"></a>

-   [`array-fas`](#org33bad3a), Function


#### R {#r}

<a id="org969f355"></a>

-   [`read-configuration-from-files`](#org1a56f80),
    Function
-   [`reset-option`](#org9da1d1d), Function
-   [`run-project`](#org0231a8e), Function
-   [`run-project/example`](#org14dfe42), Function


#### S {#s}

<a id="org0b6ee28"></a>

-   [`set-input-file`](#orga00af8c), Function
-   [`set-output-file`](#orgc3b3ee8), Function
-   [`show-classifiable-attributes`](#org86c2050),
    Function
-   [`show-classifiers`](#org533d17f), Function
-   [`show-configuration-options`](#org2fba9e2),
    Function
-   [`show-configuration-sections`](#orga9f6a57),
    Function
-   [`show-map`](#orgef7ea19), Function


#### W {#w}

<a id="org538fc7d"></a>

-   [`write-classifier`](#org3c8e2b5), Function
-   [`write-configuration`](#org756bc34), Function
-   [`write-default-configuration`](#org350ed9e),
    Function


## Colophon {#colophon}

This section of the documentation was generated from Common Lisp source code using a hacked up copy of CLOD, version 1.0.
The latest version of CLOD is available [here](http://bitbucket.org/eeeickythump/clod/).
