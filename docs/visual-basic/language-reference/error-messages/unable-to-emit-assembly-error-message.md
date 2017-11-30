---
title: "Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru volá Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu, s linkeru reporting chybu ve fázi emisí vytváření sestavení.  
  
 **ID chyby:** BC30145  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Prověřením uvozovkách chybové zprávy a podívejte se téma [Nástroj Al.exe chyby a upozornění](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) pro další vysvětlení a doporučení.  
  
2.  Zkuste se sestavení ručně, buď pomocí [Al.exe (Linker sestavení)](https://msdn.microsoft.com/library/c405shex) nebo [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23).  
  
3.  Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.  
  
### <a name="to-sign-the-assembly-manually"></a>K podepsání sestavení ručně  
  
1.  Použití [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23) k vytvoření souboru pár veřejného a privátního klíče.  
  
     Tento soubor má příponu .snk.  
  
2.  Odstraňte odkaz na modelu COM, která generuje chybu ze svého projektu.  
  
3.  Z Windows **spustit** nabídky, přejděte na příkaz **programy**, přejděte na příkaz **Microsoft Visual Studio 2008**, přejděte na příkaz **nástroje sady Visual Studio**, a pak klikněte na tlačítko **příkazový řádek sady Visual Studio 2008**.  
  
4.  Přesunout do adresáře, kam chcete umístit vaše obálku sestavení.  
  
5.  Zadejte následující kód.  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     Příklad kódu, který můžete zadat by následující.  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     Pokud cesta nebo soubor obsahuje mezery, použijte uvozovky (").  
  
6.  V [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], přidejte sestavení .NET odkaz na soubor, který jste právě vytvořili.  
  
## <a name="see-also"></a>Viz také  
 [Al.exe (Linker sestavení)](https://msdn.microsoft.com/library/c405shex)  
 [Al.exe nástroj chyby a upozornění](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [Sn.exe (nástroj pro silný název)](https://msdn.microsoft.com/library/k5b5tt23)  
 [Postupy: vytvoření páru veřejného a privátního klíče RSA](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [Kontaktujte nás](/visualstudio/ide/talk-to-us)
