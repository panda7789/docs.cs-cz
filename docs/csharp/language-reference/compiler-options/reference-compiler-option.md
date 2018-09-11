---
title: -reference (možnosti kompilátoru C#)
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
ms.openlocfilehash: 131cdf62917ab2fc8d564b85c30d13c8971e5809
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361868"
---
# <a name="-reference-c-compiler-options"></a>-reference (možnosti kompilátoru C#)
**– Referenční dokumentace** možnost způsobí, že kompilátor importovat [veřejné](../../../csharp/language-reference/keywords/public.md) zadávat informace do zadaného souboru do aktuálního projektu, což umožní k odkazování na metadata ze zadaných souborů sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název souboru obsahujícího manifest sestavení. Pokud chcete importovat více než jeden soubor, zahrnují samostatný **-odkaz** možnost pro každý soubor.  
  
 `alias`  
 Platným identifikátorem C#, která bude představovat kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete importovat z více než jeden soubor, zahrňte **– referenční dokumentace** možnost pro každý soubor.  
  
 Soubory, které importujete, musí obsahovat manifest; výstupní soubor musí být zkompilovány s jedním z [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možností jiných než [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **-r** je zkratka pro **– referenční dokumentace**.  
  
 Použití [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) importovat metadata z výstupního souboru, který nebude obsahovat manifest sestavení.  
  
 Pokud odkazujete na sestavení (sestavení A), který odkazuje na jiné sestavení (sestavení B), budete muset odkaz na sestavení B pokud:  
  
-   Typ, který používáte v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.  
  
-   Vyvolání pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B.  
  
 Použití [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) určit adresář, ve kterém se nachází jeden nebo více odkazů na sestavení. **-Lib** téma také popisuje adresáře, ve kterých kompilátor hledá sestavení.  
  
 Aby kompilátor rozpoznával typ v sestavení a ne v modulu je potřeba jej donutit k přeložení typu, což lze provést definováním instance typu. Existují jiné způsoby přeložení názvů typů v sestavení pro kompilátor: například, pokud je zděděn z typu v sestavení, název typu se pak být rozpoznatelným kompilátorem.  
  
 Někdy je potřeba odkazují na dvě různé verze stejné součásti v rámci jednoho sestavení. K tomuto účelu použít na přepínači alias **– referenční dokumentace** pro každý soubor k rozlišení mezi dvěma soubory. Tento alias se použije jako kvalifikátor pro název komponenty a vyřeší do komponenty v jednom souboru.  
  
 Csc soubor odpovědí (.rsp), který se odkazuje na běžně používá sestavení rozhraní .NET Framework, se používá ve výchozím nastavení. Použít [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Pokud nechcete, aby kompilátor používal csc.rsp.  
  
> [!NOTE]
> V sadě Visual Studio, použijte **přidat odkaz** dialogové okno. Další informace najdete v tématu [postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). K zajištění ekvivalentní chování mezi přidání odkazů pomocí `-reference` a přidání odkazů pomocí **přidat odkaz** dialogové okno, nastavte **Embed Interop Types** vlastnost **False** pro sestavení, které přidáte. **Hodnota TRUE** je výchozí hodnota pro vlastnost.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob použití [externí alias](../../../csharp/language-reference/keywords/extern-alias.md) funkce.  
  
 Kompilaci zdrojového souboru a import metadat od `grid.dll` a `grid20.dll`, které již byly zkompilovány dříve. Dvě knihovny DLL obsahovat samostatné verze stejné součásti a použijete dvě **– referenční dokumentace** s možnostmi alias pro kompilaci zdrojového souboru. Možnosti vypadat nějak takto:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Tím se nastaví externích aliasů `GridV1` a `GridV2`, který používáte ve svém programu prostřednictvím `extern` – příkaz:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Až to uděláte, můžete odkazovat na ovládací prvek mřížky z `grid.dll` vložením prefixu název ovládacího prvku s `GridV1`, tímto způsobem:  
  
```csharp  
GridV1::Grid  
```  
  
 Kromě toho můžete odkazovat na ovládací prvek mřížky z `grid20.dll` vložením prefixu název ovládacího prvku s `GridV2` tímto způsobem:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
