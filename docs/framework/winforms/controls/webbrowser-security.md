---
title: WebBrowser – zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: 957c11a085c971a81e5baa81a5b797dd53f2451a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703423"
---
# <a name="webbrowser-security"></a>WebBrowser – zabezpečení
<xref:System.Windows.Forms.WebBrowser> Ovládací prvek je navržen pro práci v režimu pouze plné důvěryhodnosti. HTML obsah zobrazený v ovládacím prvku mohou pocházet z externích webových serverů a může obsahovat nespravovaného kódu ve formě skriptů nebo webové ovládací prvky. Pokud používáte <xref:System.Windows.Forms.WebBrowser> ovládací prvek v takovém případě ovládací prvek je již méně bezpečné než Internet Explorer by ale spravovanou <xref:System.Windows.Forms.WebBrowser> ovládací prvek nezabrání spuštění takových nespravovaného kódu.  
  
 Další informace o zabezpečení problémy týkající se základního ActiveX `WebBrowser` řídí, najdete v článku [ovládací prvek WebBrowser](https://go.microsoft.com/fwlink/?LinkId=198812).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.WebBrowser>
- [Přehled ovládacího prvku WebBrowser](webbrowser-control-overview.md)
- [Ovládací prvek WebBrowser](https://go.microsoft.com/fwlink/?LinkId=198812)
