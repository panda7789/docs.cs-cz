---
description: -lib (možnosti kompilátoru C#)
title: -lib (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: e53c54dc446d9fea87a9b7a336a38ffaa31704e9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125446"
---
# <a name="-lib-c-compiler-options"></a>-lib (možnosti kompilátoru C#)
Možnost **-lib** určuje umístění sestavení, na která odkazuje, prostřednictvím možnosti [-Reference (možnosti kompilátoru C#)](./reference-compiler-option.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir1`  
 Adresář, ve kterém se má kompilátor hledat, pokud odkazované sestavení není nalezeno v aktuálním pracovním adresáři (adresář, ze kterého vyvoláváte kompilátor), nebo v adresáři systému společného jazykového modulu runtime.  
  
 `dir2`  
 Jeden nebo více dalších adresářů, ve kterých se má hledat odkazy na sestavení. Další názvy adresářů oddělujte čárkami a bez mezer mezi nimi.  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikované v následujícím pořadí:  
  
1. Aktuální pracovní adresář. Toto je adresář, ze kterého je kompilátor vyvolán.  
  
2. Systémový adresář společného jazykového modulu runtime.  
  
3. Adresáře určené parametrem **-lib**.  
  
4. Adresáře určené proměnnou prostředí LIB.  
  
 Použijte **– odkaz** k určení odkazu na sestavení.  
  
 **-lib** je doplňková; zadáním více než jednou se připojí k jakýmkoli předchozím hodnotám.  
  
 Alternativou k použití **-lib** je zkopírovat do pracovního adresáře všechna požadovaná sestavení; To vám umožní jednoduše předat název sestavení **odkazem**. Pak můžete sestavení odstranit z pracovního adresáře. Vzhledem k tomu, že cesta k závislému sestavení není zadána v manifestu sestavení, lze aplikaci spustit v cílovém počítači a vyhledat a použít sestavení v globální mezipaměti sestavení (GAC).  
  
 Vzhledem k tomu, že kompilátor může odkazovat na sestavení, neznamená, že modul CLR (Common Language Runtime) bude moci najít a načíst sestavení za běhu. Podívejte [se, jak modul runtime vyhledává sestavení](../../../framework/deployment/how-the-runtime-locates-assemblies.md) pro podrobnosti o tom, jak modul runtime vyhledává odkazovaná sestavení.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete dialogové okno **stránky vlastností** projektu.  
  
2. Klikněte na stránku vlastností **cesta k odkazům** .  
  
3. Úprava obsahu pole se seznamem.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A> .  
  
## <a name="example"></a>Příklad  
 Zkompilujte t2.cs a vytvořte soubor. exe. Kompilátor bude hledat odkazy na sestavení v pracovním adresáři a v kořenovém adresáři jednotky C.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
