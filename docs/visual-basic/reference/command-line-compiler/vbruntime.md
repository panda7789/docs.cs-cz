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
  
## <a name="arguments"></a>Arguments  
 \-  
 Zkompilujte bez odkazu na knihovnu runtime Visual Basic.  
  
 \+  
 Zkompiluje s odkazem na výchozí knihovnu runtime Visual Basic.  
  
 \*  
 Zkompilujte bez odkazu na běhovou knihovnu Visual Basic a vložte základní funkce z knihovny modulu runtime Visual Basic do sestavení.  
  
 `path`  
 Zkompiluje s odkazem na zadanou knihovnu (DLL).  
  
## <a name="remarks"></a>Poznámky  
 Možnost kompilátoru `-vbruntime` umožňuje určit, že má být kompilátor zkompilován bez odkazu na knihovnu modulu runtime Visual Basic. Pokud kompilujete bez odkazu na knihovnu prostředí Visual Basic runtime, chyby nebo upozornění jsou protokolovány v kódu nebo jazykových konstrukcích, které generují volání pomocníka modulu runtime Visual Basic. ( *Pomocník pro Visual Basic runtime* je funkce definovaná v souboru Microsoft. VisualBasic. dll, která je volána za běhu za účelem provedení konkrétní jazykové sémantiky.)  
  
 Možnost `-vbruntime+` vytváří stejné chování, k němuž dojde, pokud není zadán přepínač `-vbruntime`. Pomocí možnosti `-vbruntime+` můžete přepsat předchozí přepínače přepínačů `-vbruntime`.  
  
 Většina objektů typu `My` není při použití možností `-vbruntime-` nebo `-vbruntime:path` k dispozici.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Vkládání Visual Basic základní funkce modulu runtime  
 Možnost `-vbruntime*` umožňuje kompilovat bez odkazu na běhovou knihovnu. Místo toho je základní funkce z knihovny modulu runtime Visual Basic vložena do sestavení uživatele. Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují modul runtime Visual Basic.  
  
 Následující členové modulu runtime jsou vloženi:  
  
- @no__t – 0 – třída  
  
- @no__t – 0 – metoda  
  
- @no__t – 0 – metoda  
  
- @no__t – 0 – metoda  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbBack>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbCr>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbCrLf>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbFormFeed>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbLf>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbNewLine>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbNullChar>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbNullString>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbTab>  
  
- konstanta <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>  
  
- Některé objekty typu `My`  
  
 Pokud kompilujete pomocí možnosti `-vbruntime*` a váš kód odkazuje na člen z běhové knihovny Visual Basic, která není vložena se základní funkcí, kompilátor vrátí chybu, která označuje, že člen není k dispozici.  
  
## <a name="referencing-a-specified-library"></a>Odkazování na zadanou knihovnu  
 Můžete použít argument `path` pro zkompilování s odkazem na vlastní běhovou knihovnu namísto výchozí knihovny prostředí runtime Visual Basic.  
  
 Pokud hodnota argumentu `path` je úplná cesta k knihovně DLL, kompilátor použije tento soubor jako běhovou knihovnu. Pokud hodnota argumentu `path` není úplnou cestou k knihovně DLL, kompilátor Visual Basic v aktuální složce nejprve vyhledá identifikovanou knihovnu DLL. Pak bude hledat v cestě, kterou jste zadali pomocí možnosti kompilátoru [-SdkPath –](../../../visual-basic/reference/command-line-compiler/sdkpath.md) . Pokud není použita možnost kompilátoru `-sdkpath`, kompilátor bude hledat identifikované knihovny DLL ve složce .NET Framework (`%systemroot%\Microsoft.NET\Framework\versionNumber`).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít možnost `-vbruntime` ke kompilaci s odkazem na vlastní knihovnu.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Core – nový režim kompilace v aplikaci Visual Studio 2010 SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
