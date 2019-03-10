---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: 31323f3d5b3eed01c56476353d621cfa8fe03a12
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719114"
---
# <a name="-vbruntime"></a>-vbruntime
Určuje, že kompilátor by měl kompilovat bez odkazu do knihovny prostředí Runtime jazyka Visual Basic nebo s odkazem na knihovně modulu runtime specifické.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Proveďte kompilaci bez odkazu na knihovnu Runtime jazyka Visual Basic.  
  
 \+  
 Kompilovat s odkazem na výchozí knihovny prostředí Runtime jazyka Visual Basic.  
  
 \*  
 Proveďte kompilaci bez odkazu na knihovnu Runtime jazyka Visual Basic a vložit základní funkce z knihovny Runtime jazyka Visual Basic do sestavení.  
  
 `path`  
 Kompilovat s odkazem na zadanou knihovnu (DLL).  
  
## <a name="remarks"></a>Poznámky  
 `-vbruntime` – Možnost kompilátoru umožňuje určit, že kompilátor by měl kompilovat bez odkazu na knihovnu Runtime jazyka Visual Basic. Pokud kompilaci bez odkazu na knihovnu Runtime jazyka Visual Basic, chyby nebo varování jsou protokolovány v kódu nebo jazykové konstrukce, které generují volání pomocné rutiny modulu runtime jazyka Visual Basic. (A *pomocné rutiny modulu runtime jazyka Visual Basic* je funkce definované v souboru Microsoft.VisualBasic.dll, která je volána v době běhu k provedení konkrétní jazyk sémantického.)  
  
 `-vbruntime+` Možnost produkuje stejné chování, který nastane, pokud žádné `-vbruntime` je zadán přepínač. Můžete použít `-vbruntime+` lze přepsat předchozí `-vbruntime` přepínače.  
  
 Většina objektů `My` typu nejsou k dispozici při použití `-vbruntime-` nebo `-vbruntime:path` možnosti.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Vkládání základní funkce modulu Runtime jazyka Visual Basic  
 `-vbruntime*` Možnost umožňuje proveďte kompilaci bez odkazu na knihovnu prostředí runtime. Místo toho základní funkce z knihovny Runtime jazyka Visual Basic je vložen do sestavení uživatele. Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují modulu runtime jazyka Visual Basic.  
  
 Následující členy modulu runtime jsou vloženy:  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> Třída  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> – Metoda  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> – Metoda  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> – Metoda  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> Konstanty  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Konstanty  
  
-   Některé objekty `My` typu  
  
 Pokud kompilujete pomocí `-vbruntime*` možnost a váš kód odkazuje na člena z knihovny Runtime jazyka Visual Basic, který není integrován s základní funkce, kompilátor chybovou zprávu, která označuje, že člen není k dispozici.  
  
## <a name="referencing-a-specified-library"></a>Odkazuje na zadanou knihovnu  
 Můžete použít `path` argument pro kompilaci pomocí odkazu na knihovnu vlastního modulu runtime místo výchozí knihovny prostředí Runtime jazyka Visual Basic.  
  
 Pokud hodnota `path` argument je plně kvalifikovanou cestu ke knihovně DLL, kompilátor použije tento soubor jako knihovna prostředí runtime. Pokud hodnota `path` argument není plně kvalifikovanou cestu ke knihovně DLL, kompilátor jazyka Visual Basic vyhledá identifikované knihovny DLL ve složce aktuální nejprve. Pak bude hledat v cestě, kterou jste zadali pomocí [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) – možnost kompilátoru. Pokud `-sdkpath` není použita možnost kompilátoru, kompilátor bude hledat identifikované knihovny DLL ve složce rozhraní .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `-vbruntime` možnost kompilace s odkazem na vlastní knihovny.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Viz také:
- [Visual Basic Core – nová režim kompilace v aplikaci Visual Studio 2010 SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
