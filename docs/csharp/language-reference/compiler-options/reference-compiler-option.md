---
title: -reference (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: 3e6a999d528be111ba2b92886f4e6e3ebf185d5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173663"
---
# <a name="-reference-c-compiler-options"></a>-reference (Možnosti kompilátoru Jazyka C#)
Možnost **-reference** způsobí, že kompilátor importuje informace [o veřejném](../keywords/public.md) typu v zadaném souboru do aktuálního projektu, což vám umožní odkazovat na metadata ze zadaných souborů sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název souboru obsahujícího manifest sestavení. Chcete-li importovat více než jeden soubor, zahrňte pro každý soubor samostatnou možnost **odkazu** .  
  
 `alias`  
 Platný identifikátor Jazyka C#, který bude představovat kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li importovat z více než jednoho souboru, zahrňte pro každý soubor možnost **-reference.**  
  
 Importované soubory musí obsahovat manifest; výstupní soubor musí být zkompilován s jednou z možností [-target](./target-compiler-option.md) než [-target:module](./target-module-compiler-option.md).  
  
 **-r** je zkrácená forma **odkazu**.  
  
 Pomocí [modulu -addmodule](./addmodule-compiler-option.md) importujte metadata z výstupního souboru, který neobsahuje manifest sestavení.  
  
 Pokud odkazujete na sestavení (sestavení A), které odkazuje na jinou sestavu (sestavení B), budete muset odkazovat na sestavení B, pokud:  
  
- Typ, který použijete ze sestavení A dědí z typu nebo implementuje rozhraní z sestavení B.  
  
- Vyvoláte pole, vlastnost, událost nebo metodu, která má návratový typ nebo typ parametru ze sestavení B.  
  
 Použijte [-lib](./lib-compiler-option.md) k určení adresáře, ve kterém je umístěn jeden nebo více odkazů na sestavení. Téma **-lib** také popisuje adresáře, ve kterých kompilátor hledá sestavení.  
  
 Aby kompilátor rozpoznal typ v sestavení a nikoli v modulu, musí být vynuceno přeložit typ, který můžete provést definováním instance typu. Existují i jiné způsoby, jak přeložit názvy typů v sestavení pro kompilátor: například pokud dědíte z typu v sestavení, název typu pak bude rozpoznán kompilátorem.  
  
 Někdy je nutné odkazovat na dvě různé verze stejné součásti z jedné sestavy. Chcete-li to provést, použijte dílčí alias na **přepínači -reference** pro každý soubor k rozlišení mezi dvěma soubory. Tento alias bude použit jako kvalifikátor pro název komponenty a bude přeložit na komponentu v jednom ze souborů.  
  
 Soubor csc response (.rsp), který odkazuje na běžně používaná sestavení rozhraní .NET Framework, se používá ve výchozím nastavení. Pokud nechcete, aby kompilátor používal csc.rsp, použijte [-noconfig.](./noconfig-compiler-option.md)  
  
> [!NOTE]
> V sadě Visual Studio použijte dialogové okno **Přidat odkaz.** Další informace naleznete v [tématu How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Chcete-li zajistit ekvivalentní chování `-reference` mezi přidáváním odkazů pomocí a přidáváním odkazů pomocí dialogového okna **Přidat odkaz,** nastavte vlastnost **Embed Interop Types** na **False** pro sestavení, které přidáváte. **True** je výchozí hodnota vlastnosti.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak používat funkci [aliasu extern.](../keywords/extern-alias.md)  
  
 Zkompilovat zdrojový soubor `grid.dll` a `grid20.dll`import metadat z a , které byly zkompilovány dříve. Dvě knihovny DLL obsahují samostatné verze stejné součásti a ke kompilaci zdrojového souboru použijete dva **odkazy** s možnostmi aliasu. Možnosti vypadají takto:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Tím nastavíte externí `GridV1` `GridV2`aliasy a , které používáte `extern` v programu pomocí příkazu:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Jakmile je to hotovo, můžete odkazovat `grid.dll` na mřížku ovládacího prvku z předponou název ovládacího prvku s `GridV1`, jako je tento:  
  
```csharp  
GridV1::Grid  
```  
  
 Kromě toho můžete odkazovat na `grid20.dll` ovládací prvek mřížky `GridV2` z předponou název ovládacího prvku takto:  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
