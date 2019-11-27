---
title: '-target: appcontainerexe (C# možnosti kompilátoru)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204525"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (C# možnosti kompilátoru)
Použijete-li možnost kompilátoru **-target: appcontainerexe** , kompilátor vytvoří spustitelný soubor systému Windows (. exe), který musí být spuštěn v kontejneru aplikace. Tato možnost je ekvivalentní k [cíli: winexe](./target-winexe-compiler-option.md) , ale je navržena pro aplikace Windows 8. x Store.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete, aby aplikace běžela v kontejneru aplikace, tato možnost nastaví bit v [přenositelném spustitelném](/windows/desktop/Debug/pe-format) souboru (PE). Pokud je tento bit nastaven, dojde k chybě, pokud se metoda CreateProcess pokusí spustit spustitelný soubor mimo kontejner aplikace.  
  
 Pokud nepoužijete možnost [-out](./out-compiler-option.md) , název výstupního souboru vezme název vstupního souboru, který obsahuje metodu [Main](../../programming-guide/main-and-command-args/index.md) .  
  
 Když zadáte tuto možnost na příkazovém řádku, všechny soubory až do **Možnosti další nebo** **cíl** se použijí k vytvoření spustitelného souboru.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí  
  
1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.  
  
2. Na kartě **aplikace** v seznamu **Typ výstupu** vyberte možnost **aplikace pro Windows Store**.  
  
     Tato možnost je k dispozici pouze pro šablony aplikací Windows 8. x Store.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje `filename.cs` do spustitelného souboru systému Windows, který lze spustit pouze v kontejneru aplikace.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [-Target (C# možnosti kompilátoru)](./target-compiler-option.md)
- [-target: winexe (C# možnosti kompilátoru)](./target-winexe-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](./index.md)
