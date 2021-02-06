---
title: TTT
date: 2021-02-05 22:15:06
tags:
---

``` lisp
(defmacro d/after (feature &rest body)
  "Load BODY after FEATURE, catching errors and displaying as warnings."
  (declare (indent defun))
  `(with-eval-after-load ,feature
     (condition-case-unless-debug err
         (progn
           ,@body)
       (error
        (display-warning
         'init
         (format "%s eval-after-load: %s "
                 (symbol-name ,feature)
                 (error-message-string err))
         :error)))))
```