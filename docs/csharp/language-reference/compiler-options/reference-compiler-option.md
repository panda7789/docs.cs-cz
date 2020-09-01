---
description: -Reference (možnosti kompilátoru C#)
title: -Reference (možnosti kompilátoru C#)
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
ms.openlocfilehash: 7b84953f85545c0400c7136c258849f259e8b48a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124796"
---
# <a name="-reference-c-compiler-options"></a>-Reference (možnosti kompilátoru C#)
Možnost **-reference** způsobí, že kompilátor importuje informace o [veřejném](../keywords/public.md) typu do zadaného souboru do aktuálního projektu, takže umožňuje odkazovat na metadata ze zadaných souborů sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Název souboru obsahujícího manifest sestavení. Chcete-li importovat více než jeden soubor, zahrňte možnost samostatného **odkazu** pro každý soubor.  
  
 `alias`  
 Platný identifikátor jazyka C#, který bude představovat kořenový obor názvů, který bude obsahovat všechny obory názvů v sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li importovat z více než jednoho souboru, zahrňte možnost **-reference** pro každý soubor.  
  
 Soubory, které importujete, musí obsahovat manifest; výstupní soubor musí být zkompilován s jednou z možností [TARGETu](./target-compiler-option.md) s výjimkou [target: Module](./target-module-compiler-option.md).  
  
 **-r** je krátká forma **reference**.  
  
 Pomocí [-addmodule –](./addmodule-compiler-option.md) importujte metadata z výstupního souboru, který neobsahuje manifest sestavení.  
  
 Pokud odkazujete na sestavení (sestavení A), které odkazuje na jiné sestavení (sestavení B), budete muset odkazovat na sestavení B, pokud:  
  
- Typ, který použijete ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.  
  
- Vyvoláte pole, vlastnost, událost nebo metodu, které mají návratový typ nebo typ parametru ze sestavení B.  
  
 Pomocí [-lib](./lib-compiler-option.md) Určete adresář, ve kterém se nachází jeden nebo více odkazů na sestavení. Téma **-lib** také popisuje adresáře, ve kterých kompilátor vyhledává sestavení.  
  
 Aby mohl kompilátor rozpoznat typ v sestavení a ne v modulu, musí být vynucen přeložit typ, který lze provést definováním instance typu. Existují i jiné způsoby, jak přeložit názvy typů v sestavení pro kompilátor: například Pokud převezmete z typu v sestavení, název typu bude rozpoznán kompilátorem.  
  
 V některých případech je nutné odkazovat na dvě různé verze stejné komponenty z jednoho sestavení. Uděláte to tak, že pro každý soubor použijete dílčí možnost alias na přepínač **-reference** pro jednotlivé soubory, abyste je rozlišili mezi těmito dvěma soubory. Tento alias bude použit jako kvalifikátor pro název součásti a bude přeložen na součást v jednom ze souborů.  
  
 Ve výchozím nastavení se používá soubor odpovědí csc (. rsp), který odkazuje na běžně používaná .NET Framework sestavení. Pokud nechcete, aby kompilátor používal CSc. rsp, použijte [-li konfiguraci](./noconfig-compiler-option.md) .  
  
> [!NOTE]
> V aplikaci Visual Studio, použijte dialogové okno **Přidat odkaz** . Další informace najdete v tématu [Postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager). Chcete-li zajistit ekvivalentní chování mezi přidáním odkazů pomocí `-reference` a přidáním odkazů pomocí dialogového okna **Přidat odkaz** , nastavte vlastnost **Embed Interop Types** na **hodnotu false** pro sestavení, které přidáváte. **True** je výchozí hodnota pro vlastnost.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak použít funkci [extern alias](../keywords/extern-alias.md) .  
  
 Zdrojový soubor zkompilujete a naimportujete metadata z `grid.dll` a `grid20.dll` , které byly zkompilovány dříve. Tyto dvě knihovny DLL obsahují samostatné verze stejné komponenty a k zkompilování zdrojového souboru použijete dva **odkazy** s možnostmi aliasu. Možnosti vypadají takto:  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 Tím se nastaví externí aliasy `GridV1` a `GridV2` , které v programu použijete, prostřednictvím `extern` příkazu:  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 Až to uděláte, můžete odkazovat na ovládací prvek mřížky z `grid.dll` pomocí předpony názvu ovládacího prvku, například takto `GridV1` :  
  
```csharp  
GridV1::Grid  
```  
  
 Kromě toho můžete odkazovat na ovládací prvek mřížky z `grid20.dll` pomocí předpony názvu ovládacího prvku `GridV2` následujícím způsobem:  
  
```csharp  
GridV2::Grid
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
