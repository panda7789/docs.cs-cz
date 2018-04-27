---
title: 'Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61a5c6b753b8aa70905027bc1449739769cd8da5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Sestavení nelze vygenerovat: &lt;chybová zpráva&gt;
Visual Basic – kompilátor volání Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu, s linkeru reporting chybu ve fázi emisí vytváření sestavení.  
  
 **ID chyby:** BC30145  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Prověřením uvozovkách chybové zprávy a podívejte se téma [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). Další vysvětlení a Rady, jak.  
  
2.  Zkuste se sestavení ručně, buď pomocí [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) nebo [Sn.exe (nástroj silným názvem)](../../../framework/tools/sn-exe-strong-name-tool.md).  
  
3.  Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.  
  
### <a name="to-sign-the-assembly-manually"></a>K podepsání sestavení ručně  
  
1.  Použití [Sn.exe (nástroj silným názvem)][Sn.exe (nástroj silným názvem)](../../../framework/tools/sn-exe-strong-name-tool.md)) k vytvoření souboru pár veřejného a privátního klíče.  
  
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
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Sn.exe (nástroj pro silný název)] [Sn.exe (nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Postupy: Vytvoření páru veřejného a soukromého klíče](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Kontaktujte nás](/visualstudio/ide/talk-to-us)
