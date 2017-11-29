---
title: "-target: winmdobj (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f690591b79159a0196a1637903f2cc53442976e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="targetwinmdobj-c-compiler-options"></a>/target:winmdobj (Možnosti kompilátoru C#)
Pokud použijete **/target: winmdobj** – možnost kompilátoru, kompilátor vytvoří zprostředkující .winmdobj soubor, který můžete převést do prostředí Windows Runtime binárního souboru (.winmd) souboru. Soubor .winmd mohou být spotřebovávána pak JavaScript a C++ programy, kromě spravované jazyk programy.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/target:winmdobj  
```  
  
## <a name="remarks"></a>Poznámky  
 **Winmdobj** nastavení signály pro kompilátor, že modul zprostředkující je vyžadována. Visual Studio v odpovědi, zkompiluje jako soubor .winmdobj knihovny tříd jazyka C#. Soubor .winmdobj můžete pak dodáni prostřednictvím <xref:Microsoft.Build.Tasks.WinMDExp> exportovat nástroj k vytvoření souboru metadat (.winmd) systému Windows. Soubor .winmd obsahuje kód z původní knihovna a WinMD metadata, která se používá JavaScript nebo C++ a prostředí Windows Runtime.  
  
 Výstup tohoto souboru, který se zkompiluje pomocí **/target: winmdobj** – možnost kompilátoru je určen k použití pouze jako vstup pro nástroj pro export WimMDExp; samotný soubor .winmdobj neodkazuje přímo.  
  
 Pokud nechcete použít [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název prvního vstupního souboru. A [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda není povinné.  
  
 Pokud zadáte možnost/target: winmdobj na příkazovém řádku, všechny soubory až do dalšího **/out** nebo [/target: Module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) možnost slouží k vytvoření programu systému Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt a potom zvolte **vlastnosti**.  
  
2.  Vyberte **aplikace** kartě.  
  
3.  V **výstupní typ** vyberte **souboru WinMD**.  
  
     **Souboru WinMD** možnost je dostupná pouze pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikace.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `filename.cs` do souboru zprostředkující .winmdobj.  
  
```console  
csc /target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [/ target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)
