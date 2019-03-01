---
title: 'Postupy: Přidání více množin nastavení do vaší aplikace vC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 447d171cf9dbe2672ae138e9e902cbd72a206c94
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969634"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Postupy: Přidání více množin nastavení do vaší aplikace v jazyce C\#
V některých případech můžete chtít mít více množin nastavení v aplikaci. Například pokud vyvíjíte aplikaci kde se očekává často měnit konkrétní skupinu nastavení, může být vhodné oddělit vše do jediného souboru tak, aby soubor se dá nahradit velkoobchodních, ostatní nechat to neovlivní. Visual Studio umožňuje přidání více množin nastavení do projektu. Další sadu nastavení je možný prostřednictvím Properties.Settings objektu.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Chcete-li přidat další sadu nastavení do vaší aplikace  
  
1.  Z **projektu** nabídce zvolte **přidat novou položku**. **Přidat novou položku** zobrazí se dialogové okno.  
  
2.  V **přidat novou položku** dialogu **souboru s nastavením**, zadejte název souboru a klikněte na tlačítko **přidat** přidáte nový soubor nastavení do vašeho řešení.  
  
3.  V **Průzkumníka řešení**, přetáhněte nový soubor nastavení do **vlastnosti** složky. To umožňuje nové nastavení k dispozici v kódu.  
  
4.  Přidat a používat nastavení v tomto souboru, stejně jako jakýkoli jiný soubor nastavení. Tato skupina nastavení prostřednictvím objektu Properties.Settings můžete přistupovat.  
  
## <a name="see-also"></a>Viz také:
- [Použití nastavení aplikace a uživatelských nastavení](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
