---
title: "Postupy: Čtení uživatelských nastavení při běhu pomocí C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85dc3a2c97b8fe5003c6026874dbdcaa9af89d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
