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
ms.openlocfilehash: 4a96da3668a73368dd98055a9082479f162b7b45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218173"
---
# <a name="-reference-c-compiler-options"></a>-reference (možnosti kompilátoru C#)
**– Referenční dokumentace** možnost způsobí, že kompilátor importuje [veřejné](../../../csharp/language-reference/keywords/public.md) informací o typu do zadaného souboru do aktuálního projektu, a umožňuje odkazování na metadata ze zadaných souborů sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Název souboru obsahujícího manifest sestavení. K importu více než jeden soubor, zahrnují samostatný **– referenční dokumentace** možnost pro každý soubor.  
  
 `alias`  
 Platný C# identifikátor představující kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li importovat z více než jeden soubor, obsahovat **-odkaz** možnost pro každý soubor.  
  
 Soubory, které importujete musí obsahovat manifest; výstupní soubor musí být zkompilován s jedním z [-cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možnosti jiné než [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 **-r** je zkratka pro **– referenční dokumentace**.  
  
 Použití [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) Import metadat z výstupního souboru, který neobsahuje manifest sestavení.  
  
 Pokud odkazujete na sestavení (sestavení A), který odkazuje na jiné sestavení (sestavení B), bude muset odkaz na sestavení B pokud:  
  
-   Typ, který ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.  
  
-   Vyvolání polí, vlastnost, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B.  
  
 Použití [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) na adresář, ve kterém se nachází jeden nebo více odkazů na sestavení. **-Lib** téma také popisuje adresáře, ve kterých kompilátor vyhledává sestavení.  
  
 Aby kompilátoru rozpoznat typu v sestavení a není v modulu je nutné vynutit pro vyřešení typu, což lze provést tak, že definujete instance typu. Existují jiné způsoby přeložit názvy typů v sestavení pro kompilátor: například pokud jste dědí od typu v sestavení, název typu pak rozpozná pomocí kompilátoru.  
  
 Někdy je nezbytné k odkazování dvě různé verze stejné komponenty z v jednom sestavení. K tomu použít alias přepínači na **– referenční dokumentace** pro každý soubor k rozlišení dvou souborech. Tento alias se použije jako kvalifikátor pro název součásti a bude odkazující na komponentu v jeden ze souborů.  
  
 Soubor odpovědí (.rsp) csc, jehož odkazy běžně používají sestavení rozhraní .NET Framework, se používá ve výchozím nastavení. Použít [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Pokud nechcete, aby kompilátor používal csc.rsp.  
  
> [!NOTE]
> V sadě Visual Studio, použijte **přidat odkaz na** dialogové okno. Další informace najdete v tématu [postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Zajistit ekvivalentní chování mezi přidání odkazů pomocí `-reference` a přidání odkazů pomocí **přidat odkaz na** dialogové okno, sada **vložit zprostředkovatel komunikace s objekty typy** vlastnost **False** pro sestavení, které přidáváte. **Hodnota TRUE,** je výchozí hodnota pro vlastnost.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob použití [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) funkce.  
  
 Kompilaci zdrojového souboru a importovat metadata z `grid.dll` a `grid20.dll`, které byly zkompilovány dříve. Tyto dvě knihovny obsahují samostatné verze stejné komponenty, a použijte dva **– referenční dokumentace** s možnostmi alias pro kompilaci zdrojového souboru. Možnosti vypadat takto:  
  
 -reference:GridV1=grid.dll a - reference:GridV2=grid20.dll  
  
 Toto nastaví externí aliasy "GridV1" a "GridV2", které použijete v programu prostřednictvím externího příkazu:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Až bude vše Hotovo, najdete do ovládacího prvku mřížky z grid.dll pomocí prefixu název ovládacího prvku s GridV1, například takto:  
  
```csharp  
GridV1::Grid  
```  
  
 Kromě toho najdete do ovládacího prvku mřížky z grid20.dll pomocí prefixu název ovládacího prvku GridV2 takto:  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
