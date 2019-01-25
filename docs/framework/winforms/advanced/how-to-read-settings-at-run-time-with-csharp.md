---
title: 'Postupy: Čtení uživatelských nastavení při běhu pomocíC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d798b40e5e337ea7652c8e82cb7fa860a87528b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521748"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>Postupy: Čtení uživatelských nastavení při běhu pomocíC# #
Nastavení oboru aplikace i s rozsahem uživatele si můžete přečíst v době běhu pomocí objektu vlastností. Objekt vlastností zpřístupní všechna výchozí nastavení projektu prostřednictvím Properties.Settings.Default člena.  
  
### <a name="to-read-settings-at-run-time-with-c"></a>Chcete-li čtení uživatelských nastavení při běhu pomocíC#  
  
-   Přístup k příslušné nastavení prostřednictvím Properties.Settings.Default člena. Následující příklad ukazuje, jak přiřadit nastavení s názvem `myColor` vlastnosti BackColor. Vyžaduje, abyste vytvořili soubor nastavení obsahující nastavení s názvem `myColor` typu `System.Drawing.Color`. Informace o vytvoření souboru nastavení najdete v tématu [How To: Vytvoření nového nastavení při návrhu](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md).  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Použití nastavení aplikace a uživatelských nastavení](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Postupy: Zápis uživatelských nastavení při běhu pomocíC#](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)
- [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
