---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocí C#'
description: Přečtěte si, jak číst nastavení s rozsahem aplikace i s uživatelským rozsahem v době běhu v jazyce C# prostřednictvím objektu Properties.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903348"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Postupy: čtení nastavení v době běhu pomocí jazyka C\#

Pomocí objektu Properties lze v době běhu číst nastavení s rozsahem aplikace i uživatele s rozsahem. Objekt Properties zpřístupňuje všechna výchozí nastavení pro projekt prostřednictvím vlastností. Settings. Default ve výchozím oboru názvů projektu, ve kterém jsou definovány.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Čtení nastavení v době běhu pomocí jazyka C\#
  
Přístup k příslušnému nastavení získáte prostřednictvím vlastnosti. Settings. default. Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` k vlastnosti BackColor. Vyžaduje, abyste předtím vytvořili soubor nastavení obsahující nastavení s názvem `myColor` typu `System.Drawing.Color` . Informace o vytvoření souboru nastavení najdete v tématu [Postup: vytvoření nového nastavení v době návrhu](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Viz také

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Postupy: Zápis uživatelských nastavení při běhu pomocí C#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
