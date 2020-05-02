---
title: GUI Emacs向けのconfig
---

自分用のEmacs (GUI) 向けのconfigを残しておく.

# exec-path-from-shell
```
(use-package exec-path-from-shell
  :if (memq window-system '(mac ns))
  :config
  (exec-path-from-shell-initialize))
```

# solarized-theme
```
(use-package solarized-theme
  :if window-system
  :custom
  (solarized-scale-org-headlines nil)
  :config
  (load-theme 'solarized-dark t))
```

# Font
```
;; 11223344556677889910
;; 壱弐参四五六七八九拾
(when window-system
  (when (eq system-type 'darwin)
    (create-fontset-from-ascii-font "Menlo-14" nil "menlo")
    (set-fontset-font "fontset-menlo" 'unicode "Hiragino Maru Gothic ProN W4-16" nil 'append)
    (add-to-list 'default-frame-alist '(font . "fontset-menlo")))
  (when (memq system-type '(gnu gnu/linux gnu/kfreebsd))
    (create-fontset-from-ascii-font "Dejavu Sans Mono-12:weight=normal:slant=normal" nil "dejavu")
    (set-fontset-font "fontset-dejavu" 'unicode "IPAGothic-15" nil 'append)
    (add-to-list 'default-frame-alist '(font . "fontset-dejavu")))
  (setq frame-inherited-parameters '(font tool-bar-lines)))
```
