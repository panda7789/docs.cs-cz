---
title: 'Postupy: Přidání více množin nastavení do vaší aplikace v C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 029dffc878c62613e291620a2bd86971f369d15a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Postupy: Přidání více množin nastavení do vaší aplikace v C# #
V některých případech můžete chtít mít více sad nastavení v aplikaci. Například pokud vyvíjíte aplikace kde je očekávána určité skupiny nastavení, chcete-li změnit často, může být vhodné k oddělení všechny do jednoho souboru tak, aby soubor můžete nahradit velkoobchodních, a další nastavení neovlivní. Visual Studio můžete k přidání více množin nastavení do projektu. Další sad nastavení je možné přistupovat prostřednictvím objektu Properties.Settings.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Chcete-li přidat další sadu nastavení do vaší aplikace  
  
1.  Z **projektu** nabídce zvolte **přidat novou položku**. **Přidat novou položku** otevře se dialogové okno.  
  
2.  V **přidat novou položku** dialogové okno, vyberte **soubor nastavení**, zadejte název souboru a klikněte na tlačítko **přidat** přidat nový soubor nastavení vašeho řešení.  
  
3.  V **Průzkumníku řešení**, přetáhněte ji do nový soubor s nastaveními **vlastnosti** složky. To umožňuje nové nastavení k dispozici v kódu.  
  
4.  Přidat a používat nastavení v tomto souboru, stejně jako jakýkoli jiný soubor nastavení. Tato skupina nastavení prostřednictvím objektu Properties.Settings můžete přistupovat.  
  
## <a name="see-also"></a>Viz také  
 [Použití nastavení aplikace a uživatelských nastavení](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
