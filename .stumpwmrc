(in-package :stumpwm)

(require :swank)
(swank-loader:init)
(swank:create-server :port 4004
                     :style swank:*communication-style*
                     :dont-close t)
(defcommand toggle-modeline () ()
"Toggle mode line."
(stumpwm:toggle-mode-line (stumpwm:current-screen) (stumpwm:current-head)))

(init-load-path "~/stumpwm/contrib/")
(load-module "battery-portable")
(load-module "cpu")


(set-prefix-key (kbd "C-z"))
(setf *mode-line-foreground-color* "Green")
(setf *mode-line-background-color* "Black")
(setf *mode-line-timeout* 1)
(setf *screen-mode-line-format*
      (list "%w | %B | %t %f | "
            '(:eval (run-shell-command "date" t))))
(toggle-modeline)
(setf *message-window-gravity* :center)
(setf *input-window-gravity* :center)
(set-bg-color "Black")
(set-fg-color "Green")

(defcommand firefox () ()
  "start firefox or switch to it if already running."
  (run-or-raise "firefox" '(:class "Firefox")))
(define-key *root-map* (kbd "x") "firefox")

 (defcommand duck (search)
 ((:string "Search in DuckDuckGo for: "))
  "prompt the user for a search term and look it up in DuckDuckGo "
  (check-type search string)
  (run-shell-command (format nil "xdg-open \"https://duckduckgo.com?q=~a\"" search)))
