---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocí C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: 8259e2f429718793c01868855651d1000620fae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Postupy: Čtení uživatelských nastavení při běhu pomocí C# #
Nastavení brány obor aplikace a nastavení uživatele si můžete přečíst v době běhu prostřednictvím vlastnosti objektu. Objekt vlastností zpřístupní všechna výchozí nastavení pro projekt prostřednictvím Properties.Settings.Default člena.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Číst nastavení při běhu pomocí C#  
  
-   Přístup k příslušné nastavení prostřednictvím Properties.Settings.Default člena. Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` na vlastnost Barva pozadí. Vyžaduje, abyste vytvořili nastavení souboru, který obsahuje nastavení s názvem `myColor` typu `System.Drawing.Color`. Informace o vytvoření souboru nastavení najdete v tématu [postupy: vytvoření nového nastavení v době návrhu](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Použití nastavení aplikace a uživatelských nastavení](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Postupy: Zápis uživatelských nastavení při běhu pomocí C#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
