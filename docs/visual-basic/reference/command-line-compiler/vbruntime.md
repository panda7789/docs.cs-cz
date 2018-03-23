---
title: -vbruntime
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6c6529fabddc75fb6ac751e0314011f05db7869
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-vbruntime"></a>-vbruntime
Určuje, že by měl kompilátor kompilovat bez odkaz na Visual Basic Runtime Library nebo s odkazem na knihovnu konkrétní runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Kompilovat bez odkaz na Visual Basic Runtime Library.  
  
 \+  
 Kompilace s odkazem na výchozí hodnoty jazyka Visual Basic Runtime Library.  
  
 \*  
 Kompilovat bez odkazu na Visual Basic Runtime Library a vložit základní funkce z Visual Basic Runtime Library do sestavení.  
  
 `path`  
 Kompilovat s odkazem na uvedené knihovny (DLL).  
  
## <a name="remarks"></a>Poznámky  
 `-vbruntime` – Možnost kompilátoru umožňuje určit, že by měl kompilátor kompilovat bez odkazu na Visual Basic Runtime Library. Pokud zkompilujete bez odkazu na Visual Basic Runtime Library, chyby nebo upozornění kód nebo jazyk konstrukce, které generují volání pomocné rutiny modulu runtime jazyka Visual Basic přihlášeni. (A *jazyka Visual Basic runtime pomocná* je funkci definovanou v souboru Microsoft.VisualBasic.dll, která je volána v době běhu k provedení sémantického konkrétní jazyk.)  
  
 `-vbruntime+` Možnost vytváří stejné chování, k níž dojde, pokud žádné `-vbruntime` je zadán přepínač. Můžete použít `-vbruntime+` možnost přepsat předchozí `-vbruntime` přepínače.  
  
 Většina objekty `My` typu nejsou k dispozici při použití `-vbruntime-` nebo `-vbruntime:path` možnosti.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Vložení základní funkce Runtime jazyka Visual Basic  
 `-vbruntime*` Možnost umožňuje kompilovat bez odkaz na knihovnu runtime. Místo toho základní funkce z Visual Basic Runtime Library vložené v sestavení uživatele. Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují runtime jazyka Visual Basic.  
  
 Následující členy runtime jsou vloženy:  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> – Třída  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> – Metoda  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> – Metoda  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> – Metoda  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> Konstantní  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> Konstantní  
  
-   Některé objekty `My` typu  
  
 Pokud zkompilujete pomocí `-vbruntime*` možnost a váš kód odkazuje na člena z Visual Basic Runtime Library, který není vložených s základní funkce, kompilátor vrátí chybu, která určuje, že člen není k dispozici.  
  
## <a name="referencing-a-specified-library"></a>Odkazování na uvedené knihovny  
 Můžete použít `path` argument zkompilovat s odkazem na knihovnu vlastní runtime místo výchozího Visual Basic Runtime Library.  
  
 Pokud hodnota `path` argument je plně kvalifikovanou cestu ke knihovně DLL, kompilátor použije tento soubor jako knihovna runtime. Pokud hodnota `path` argument není plně kvalifikovaná cesta ke knihovně DLL, Visual Basic – kompilátor bude hledat identifikovaných DLL v aktuální složce nejdřív. Bude poté hledat v cestě, která jste zadali pomocí [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) – možnost kompilátoru. Pokud `-sdkpath` – možnost kompilátoru nepoužívá, kompilátor bude hledat identifikovaných knihovny DLL ve složce rozhraní .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `-vbruntime` kompilovat s odkazem na knihovnu vlastní možnost.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Základní jazyka Visual Basic – nový režim kompilace v sadě Visual Studio 2010 SP1](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
