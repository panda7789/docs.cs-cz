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
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005056"
---
# <a name="-vbruntime"></a>-vbruntime
Určuje, že má kompilátor kompilovat bez odkazu na knihovnu modulu runtime Visual Basic, nebo s odkazem na konkrétní běhovou knihovnu.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Argumenty  
 \-  
 Zkompilujte bez odkazu na knihovnu runtime Visual Basic.  
  
 \+  
 Zkompiluje s odkazem na výchozí knihovnu runtime Visual Basic.  
  
 \*  
 Zkompilujte bez odkazu na běhovou knihovnu Visual Basic a vložte základní funkce z knihovny modulu runtime Visual Basic do sestavení.  
  
 `path`  
 Zkompiluje s odkazem na zadanou knihovnu (DLL).  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-vbruntime` kompilátoru umožňuje určit, zda má být kompilátor zkompilován bez odkazu na knihovnu modulu runtime Visual Basic. Pokud kompilujete bez odkazu na knihovnu prostředí Visual Basic runtime, chyby nebo upozornění jsou protokolovány v kódu nebo jazykových konstrukcích, které generují volání pomocníka modulu runtime Visual Basic. ( *Pomocník pro Visual Basic runtime* je funkce definovaná v souboru Microsoft. VisualBasic. dll, která je volána za běhu za účelem provedení konkrétní jazykové sémantiky.)  
  
 `-vbruntime+` Možnost vytvoří stejné chování, které nastane, pokud není `-vbruntime` zadán žádný přepínač. K přepsání předchozích `-vbruntime+` `-vbruntime` přepínačů můžete použít možnost.  
  
 Většina objektů `My` typu není k dispozici, `-vbruntime-` Pokud používáte možnosti nebo `-vbruntime:path` .  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Vkládání Visual Basic základní funkce modulu runtime  
 `-vbruntime*` Možnost umožňuje kompilovat bez odkazu na běhovou knihovnu. Místo toho je základní funkce z knihovny modulu runtime Visual Basic vložena do sestavení uživatele. Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují modul runtime Visual Basic.  
  
 Následující členové modulu runtime jsou vloženi:  
  
- Třída <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
- Metoda <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
- <xref:Microsoft.VisualBasic.Constants.vbBack>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbCr>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbCrLf>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbFormFeed>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbLf>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbNewLine>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullChar>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullString>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbTab>změnil  
  
- <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>změnil  
  
- Některé objekty `My` typu  
  
 Pokud kompilujete pomocí `-vbruntime*` možnosti a váš kód odkazuje na člen z knihovny Visual Basic runtime, která není vložena se základními funkcemi, kompilátor vrátí chybu, která indikuje, že člen není k dispozici.  
  
## <a name="referencing-a-specified-library"></a>Odkazování na zadanou knihovnu  
 `path` Argument můžete použít ke kompilaci s odkazem na vlastní běhovou knihovnu namísto výchozí knihovny runtime Visual Basic.  
  
 Pokud je hodnota `path` argumentu plně kvalifikovaná cesta k knihovně DLL, kompilátor použije tento soubor jako běhovou knihovnu. Pokud hodnota `path` argumentu není úplná cesta k knihovně DLL, kompilátor Visual Basic v aktuální složce nejprve vyhledá IDENTIFIKOVANOU knihovnu DLL. Pak bude hledat v cestě, kterou jste zadali pomocí možnosti kompilátoru [-SdkPath –](../../../visual-basic/reference/command-line-compiler/sdkpath.md) . Pokud není `-sdkpath` použita možnost kompilátoru, kompilátor bude hledat identifikované knihovny DLL ve složce .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `-vbruntime` možnost ke kompilaci s odkazem na vlastní knihovnu.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Core – nový režim kompilace v aplikaci Visual Studio 2010 SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [– SdkPath –](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
