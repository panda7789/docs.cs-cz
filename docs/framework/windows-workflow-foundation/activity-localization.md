---
title: Lokalizace aktivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccabcda9e26751db80ee7e955458d0eee0cae7e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="activity-localization"></a>Lokalizace aktivity
Pokud pracovní postup aplikace a součásti potenciální lokalizovat do jiných jazykové verze a jazyky, řetězce prostředků je třeba použít tak, aby mohly být lokalizovány bez nutnosti rekompilace.  
  
## <a name="activity-localization"></a>Lokalizace aktivity  
 Jako u všech aplikací, které musí být lokalizovaný (vydané v různých verzích pro různé jazyky a kultur), všechny řetězce, které se zobrazí uživateli by neměl být put přímo v kódu, ale spíš uložené v souboru prostředků. Řetězce lze přistupovat prostřednictvím <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`. Pokud vyvíjíte komponenty, která se distribuuje v několika jazycích, chcete taky použít řetězce prostředků pro aktivity ověřovacích zpráv, uživatelem definované sledování dat trasování zprávy a také chybové zprávy.  
  
 Následujícím cvičení ukazuje, jak pomocí zdrojového souboru.  
  
#### <a name="using-resource-files-for-localized-strings"></a>Použití zdrojových souborů pro lokalizované řetězce  
  
1.  V [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a vyberte **přidat...** , **Novou položku...** .  
  
2.  Vyberte **souboru prostředků** a název souboru ErrorResources.resx. Klikněte na tlačítko **přidat**.  
  
3.  Otevřete soubor prostředků. Přidat novou položku s **název** z ErrorString a **hodnotu** z "aktivity není platný."  
  
4.  Přidejte následující `using` příkazy ke třídě.  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  Vytvořte prostředek manager ve vašem projektu.  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  Získáte řetězec ze Správce prostředků, kdy je potřeba.  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 Následující příklad kódu ukazuje, jak využívat lokalizovaných řetězců v <xref:System.Activities.Activity.CacheMetadata%2A> metoda.  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
