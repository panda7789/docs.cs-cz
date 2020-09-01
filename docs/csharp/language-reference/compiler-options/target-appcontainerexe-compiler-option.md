---
description: '-target: appcontainerexe (možnosti kompilátoru C#)'
title: '-target: appcontainerexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 8c3b85c2f5a20788bd311e9bf3b300c32967da77
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128579"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (možnosti kompilátoru C#)
Použijete-li možnost kompilátoru **-target: appcontainerexe** , kompilátor vytvoří spustitelný soubor systému Windows (. exe), který musí být spuštěn v kontejneru aplikace. Tato možnost je ekvivalentní k [cíli: winexe](./target-winexe-compiler-option.md) , ale je navržena pro aplikace Windows 8. x Store.  
  
## <a name="syntax"></a>Syntax  
  
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
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .  
  
## <a name="example"></a>Příklad  
 Následující příkaz se zkompiluje `filename.cs` do spustitelného souboru systému Windows, který lze spustit pouze v kontejneru aplikace.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Viz také

- [-Target (možnosti kompilátoru C#)](./target-compiler-option.md)
- [-target: winexe (možnosti kompilátoru C#)](./target-winexe-compiler-option.md)
- [Možnosti kompilátoru C#](./index.md)
