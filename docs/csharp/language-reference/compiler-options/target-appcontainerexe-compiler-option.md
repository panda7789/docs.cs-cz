---
title: '-target: appcontainerexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: b8765f64aeb08d816ca17fce64c13e981d85145b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216736"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (možnosti kompilátoru C#)
Pokud použijete **-target: appcontainerexe** – možnost kompilátoru, kompilátor vytvoří spustitelný soubor (.exe) soubor systému Windows, který musí být spuštěn v kontejnerem aplikace. Tato možnost je ekvivalentní [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale je určená pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete vyžadovat aplikaci spustit v kontejnerem aplikace, tento parametr nastaví trochu v [přenosné spustitelný soubor](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) souboru (PE). Pokud je nastaven daný bit, dojde k chybě, pokud se pokusí spustit spustitelný soubor mimo kontejnerem aplikace CreateProcess – metoda.  
  
 Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.  
  
 Pokud tuto možnost na příkazovém řádku zadáte, všechny soubory až do dalšího **-out** nebo **-cíl** možnost slouží k vytváření spustitelný soubor.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt a potom zvolte **vlastnosti**.  
  
2.  Na **aplikace** ve **výstupní typ** vyberte **aplikace pro Windows Store**.  
  
     Tato možnost je dostupná pouze pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikace.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `filename.cs` do Windows spustitelný soubor, který lze spustit pouze v kontejnerem aplikace.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [-target: winexe (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
