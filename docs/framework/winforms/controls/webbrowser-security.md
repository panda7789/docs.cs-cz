---
title: WebBrowser – zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: b25cabca050d06dbfe97c563eb56622d1f21be54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095252"
---
# <a name="webbrowser-security"></a>WebBrowser – zabezpečení
<xref:System.Windows.Forms.WebBrowser> ovládací prvek je navržený tak, aby fungoval pouze v plné důvěryhodnosti. Obsah HTML zobrazený v ovládacím prvku může pocházet z externích webových serverů a může obsahovat nespravovaný kód ve formě skriptů nebo webových ovládacích prvků. Použijete-li ovládací prvek <xref:System.Windows.Forms.WebBrowser> v této situaci, není ovládací prvek méně zabezpečený než aplikace Internet Explorer, ale spravovaný <xref:System.Windows.Forms.WebBrowser> ovládací prvek nebrání v běhu tohoto nespravovaného kódu.  
  
 Další informace o problémech se zabezpečením souvisejícím s podkladovým ovládacím prvkem ActiveX `WebBrowser` najdete v tématu [ovládací prvek WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.WebBrowser>
- [Přehled ovládacího prvku WebBrowser](webbrowser-control-overview.md)
- [Ovládací prvek WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))
