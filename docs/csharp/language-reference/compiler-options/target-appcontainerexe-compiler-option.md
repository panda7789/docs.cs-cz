---
title: '-target: appcontainerexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 4f8c59d94b76dd0f3415846f7e682d62cc1771ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707606"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (možnosti kompilátoru C#)
Pokud používáte **-target: appcontainerexe** – možnost kompilátoru, kompilátor vytvoří spustitelný soubor (.exe) soubor Windows, který musí být spuštěn v kontejneru aplikace. Tato možnost je ekvivalentní k [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale je navržená pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Vyžadovat spuštění v kontejneru aplikace, tato možnost nastaví bit v [přenosný spustitelný soubor](/windows/desktop/Debug/pe-format) souboru (PE). Pokud je tento bit nastaven, dojde k chybě, pokud se metoda CreateProcess snaží spustit spustitelný soubor mimo kontejner aplikace.  
  
 Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.  
  
 Pokud zadáte tuto možnost příkazového řádku, všechny soubory až do další **-out** nebo **– cíl** slouží k vytvoření spustitelného souboru.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.  
  
2.  Na **aplikace** kartě **typ výstupu** klikněte na položku **aplikace Windows Store**.  
  
     Tato možnost je dostupná jenom pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikací.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz kompiluje `filename.cs` do Windows spustitelného souboru, který lze spustit pouze v kontejneru aplikace.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-target (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [-target: winexe (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
