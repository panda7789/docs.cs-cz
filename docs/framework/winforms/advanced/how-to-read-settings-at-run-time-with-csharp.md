---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocíC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8cdc1a79f1ab327ae037cd6a04aa769196405127
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974845"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Postupy: Čtení uživatelských nastavení při běhu pomocí C\#

Nastavení oboru aplikace i s rozsahem uživatele si můžete přečíst v době běhu pomocí objektu vlastností. Objekt vlastností zpřístupní všechna výchozí nastavení projektu prostřednictvím Properties.Settings.Default člena.  
  
## <a name="to-read-settings-at-run-time-with-c"></a>Chcete-li čtení uživatelských nastavení při běhu pomocí C\#
  
Přístup k příslušné nastavení prostřednictvím Properties.Settings.Default člena. Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` vlastnosti BackColor. Vyžaduje, abyste vytvořili soubor nastavení obsahující nastavení s názvem `myColor` typu `System.Drawing.Color`. Informace o vytvoření souboru nastavení najdete v tématu [How To: Vytvoření nového nastavení při návrhu](how-to-create-a-new-setting-at-design-time.md).  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>Viz také:

- [Použití nastavení aplikace a uživatelských nastavení](using-application-settings-and-user-settings.md)
- [Postupy: Zápis uživatelských nastavení při běhu pomocíC#](how-to-write-user-settings-at-run-time-with-csharp.md)
- [Přehled nastavení aplikace](application-settings-overview.md)
