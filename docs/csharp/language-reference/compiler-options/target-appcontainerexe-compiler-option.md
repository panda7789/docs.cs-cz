---
title: -target:appcontainerexe (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204525"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe (Možnosti kompilátoru Jazyka C#)
Pokud použijete možnost kompilátoru **-target:appcontainerexe,** kompilátor vytvoří soubor spustitelného souboru systému Windows (.exe), který musí být spuštěn v kontejneru aplikace. Tato možnost je ekvivalentní [-target:winexe,](./target-winexe-compiler-option.md) ale je určena pro aplikace pro Windows 8.x Store.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vyžadovat, aby aplikace běžela v kontejneru aplikace, tato možnost nastaví bit v souboru [Přenosného spustitelného souboru](/windows/desktop/Debug/pe-format) (PE). Pokud je tento bit nastaven, dojde k chybě, pokud se metoda CreateProcess pokusí spustit spustitelný soubor mimo kontejner aplikace.  
  
 Pokud nepoužijete možnost [-out,](./out-compiler-option.md) název výstupního souboru přebírá název vstupního souboru, který obsahuje metodu [Main.](../../programming-guide/main-and-command-args/index.md)  
  
 Zadáte-li tuto možnost na příkazovém řádku, budou k vytvoření spustitelného souboru použity všechny soubory až do další volby **-out** nebo **-target.**  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí  
  
1. V **Průzkumníku řešení**otevřete místní nabídku projektu a pak zvolte **Vlastnosti**.  
  
2. Na kartě **Aplikace** v seznamu **Typ výstupu** zvolte **Aplikaci pro Windows Store**.  
  
     Tato možnost je dostupná jenom pro šablony aplikací pro Windows 8.x Store.  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Následující příkaz se `filename.cs` zkompiluje do spustitelného souboru systému Windows, který lze spustit pouze v kontejneru aplikace.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-target (Možnosti kompilátoru Jazyka C#)](./target-compiler-option.md)
- [-target:winexe (Možnosti kompilátoru Jazyka C#)](./target-winexe-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
