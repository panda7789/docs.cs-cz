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
ms.openlocfilehash: 31b719fb7e43cdd6ac44424b359999410dd608a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403041"
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
 `-vbruntime`Možnost kompilátoru umožňuje určit, zda má být kompilátor zkompilován bez odkazu na knihovnu modulu Runtime Visual Basic. Pokud kompilujete bez odkazu na knihovnu prostředí Visual Basic runtime, chyby nebo upozornění jsou protokolovány v kódu nebo jazykových konstrukcích, které generují volání pomocníka modulu runtime Visual Basic. ( *Pomocník pro Visual Basic runtime* je funkce definovaná v souboru Microsoft. VisualBasic. dll, která je volána za běhu za účelem provedení konkrétní jazykové sémantiky.)  
  
 `-vbruntime+`Možnost vytvoří stejné chování, které nastane, pokud `-vbruntime` není zadán žádný přepínač. `-vbruntime+`K přepsání předchozích přepínačů můžete použít možnost `-vbruntime` .  
  
 Většina objektů `My` typu není k dispozici, pokud používáte `-vbruntime-` Možnosti nebo `-vbruntime:path` .  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Vkládání Visual Basic základní funkce modulu runtime  
 `-vbruntime*`Možnost umožňuje kompilovat bez odkazu na běhovou knihovnu. Místo toho je základní funkce z knihovny modulu runtime Visual Basic vložena do sestavení uživatele. Tuto možnost můžete použít, pokud vaše aplikace běží na platformách, které neobsahují modul runtime Visual Basic.  
  
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
  
 Pokud kompilujete pomocí `-vbruntime*` Možnosti a váš kód odkazuje na člen z knihovny Visual Basic runtime, která není vložena se základními funkcemi, kompilátor vrátí chybu, která indikuje, že člen není k dispozici.  
  
## <a name="referencing-a-specified-library"></a>Odkazování na zadanou knihovnu  
 Argument můžete použít `path` ke kompilaci s odkazem na vlastní běhovou knihovnu namísto výchozí knihovny runtime Visual Basic.  
  
 Pokud `path` je hodnota argumentu plně kvalifikovaná cesta k knihovně DLL, kompilátor použije tento soubor jako běhovou knihovnu. Pokud hodnota `path` argumentu není úplná cesta k knihovně DLL, kompilátor Visual Basic v aktuální složce nejprve vyhledá identifikovanou knihovnu DLL. Pak bude hledat v cestě, kterou jste zadali pomocí možnosti kompilátoru [-SdkPath –](sdkpath.md) . Pokud není `-sdkpath` použita možnost kompilátoru, kompilátor bude hledat identifikované knihovny DLL ve složce .NET Framework ( `%systemroot%\Microsoft.NET\Framework\versionNumber` ).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `-vbruntime` možnost ke kompilaci s odkazem na vlastní knihovnu.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Core – nový režim kompilace v aplikaci Visual Studio 2010 SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)
