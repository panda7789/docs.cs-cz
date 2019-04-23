---
title: 'Postupy: Přidání více množin nastavení do vaší aplikace v C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 9a4913f635204aac2214d97225c7b8147c6fe9ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326603"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Postupy: Přidání více množin nastavení do vaší aplikace v jazyce C\#
V některých případech můžete chtít mít více množin nastavení v aplikaci. Například pokud vyvíjíte aplikaci kde se očekává často měnit konkrétní skupinu nastavení, může být vhodné oddělit vše do jediného souboru tak, aby soubor se dá nahradit velkoobchodních, ostatní nechat to neovlivní. Visual Studio umožňuje přidání více množin nastavení do projektu. Další sadu nastavení je možný prostřednictvím Properties.Settings objektu.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Chcete-li přidat další sadu nastavení do vaší aplikace  
  
1. Z **projektu** nabídce zvolte **přidat novou položku**. **Přidat novou položku** zobrazí se dialogové okno.  
  
2. V **přidat novou položku** dialogu **souboru s nastavením**, zadejte název souboru a klikněte na tlačítko **přidat** přidáte nový soubor nastavení do vašeho řešení.  
  
3. V **Průzkumníka řešení**, přetáhněte nový soubor nastavení do **vlastnosti** složky. To umožňuje nové nastavení k dispozici v kódu.  
  
4. Přidat a používat nastavení v tomto souboru, stejně jako jakýkoli jiný soubor nastavení. Tato skupina nastavení prostřednictvím objektu Properties.Settings můžete přistupovat.  
  
## <a name="see-also"></a>Viz také:

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
