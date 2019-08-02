---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocí C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 6a40718d57fad4041eeea2fded03b7256abbe8d1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710230"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Postupy: Čtení nastavení za běhu pomocí jazyka C\#

Pomocí objektu Properties lze v době běhu číst nastavení s rozsahem aplikace i uživatele s rozsahem. Objekt Properties zpřístupňuje všechna výchozí nastavení pro projekt prostřednictvím vlastností. Settings. Default ve výchozím oboru názvů projektu, ve kterém jsou definovány.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Čtení nastavení v době běhu pomocí jazyka C\#
  
Přístup k příslušnému nastavení získáte prostřednictvím vlastnosti. Settings. default. Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` k vlastnosti BackColor. Vyžaduje, abyste předtím vytvořili soubor nastavení obsahující nastavení s názvem `myColor` typu. `System.Drawing.Color` Informace o vytvoření souboru nastavení naleznete v tématu [How to: Vytvořte nové nastavení v době](how-to-create-a-new-setting-at-design-time.md)návrhu.  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Postupy: Zápis uživatelských nastavení v době běhu pomocíC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
