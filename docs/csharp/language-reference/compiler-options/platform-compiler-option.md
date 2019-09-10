---
title: -Platform (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849877"
---
# <a name="-platform-c-compiler-options"></a>-Platform (C# možnosti kompilátoru)

Určuje, která verze modulu CLR (Common Language Runtime) může spustit sestavení.

## <a name="syntax"></a>Syntaxe

```console
-platform:string
```

## <a name="parameters"></a>Parametry

`string` \
anycpu (výchozí), anycpu32bitpreferred, ARM, x64, x86 nebo Itanium.

## <a name="remarks"></a>Poznámky

- **anycpu** (výchozí) zkompiluje sestavení tak, aby běželo na libovolné platformě. Vaše aplikace běží jako 64 proces, kdykoli je to možné, a vrátí se do 32-bit, pokud je k dispozici pouze tento režim.

- **anycpu32bitpreferred** zkompiluje vaše sestavení tak, aby běželo na libovolné platformě. Vaše aplikace běží v 32ovém režimu v systémech, které podporují 64 i 32-bit aplikací. Tuto možnost lze zadat pouze pro projekty, které cílí na .NET Framework 4,5.

- **ARM** zkompiluje vaše sestavení tak, aby běželo na počítači, který má procesor Advanced RISC Machine (ARM).

- **ARM64** zkompiluje sestavení tak, aby běželo 64 CLR na počítači, který má procesor Advanced RISC Machine (ARM), který podporuje instrukční sadu A64.

- **x64** kompiluje vaše sestavení tak, aby bylo spuštěno pomocí 64 CLR v počítači, který podporuje INSTRUKČNÍ sady amd64 nebo EM64T.

- **x86** zkompiluje vaše sestavení tak, aby se spouštělo pomocí 32 CLR kompatibilního s platformou x86.

- **Procesory Itanium** zkompiluje vaše sestavení tak, aby bylo spuštěno pomocí 64 CLR v počítači s procesorem Itanium.

V 64 operačním systému Windows:

- Sestavení kompilována s **platformou: x86** se spustí v 32 CLR spuštěném v WOW64.

- Knihovna DLL kompilovaná s **platformou-Platform: anycpu** se spouští na stejném CLR jako proces, do kterého je načtený.

- Spustitelné soubory, které jsou kompilovány s **platformou-Platform: anycpu** , se spustí v 64 modulu CLR.

- Spustitelné soubory kompilované s **platformou: anycpu32bitpreferred** se spustí na 32 CLR.

Nastavení **anycpu32bitpreferred** je platné pouze pro spustitelný soubor (. Soubory EXE) a vyžaduje .NET Framework 4,5.

Další informace o vývoji aplikace pro spuštění v operačním systému Windows 64 naleznete v tématu [64-bitové aplikace](../../../framework/64-bit-apps.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete stránku **vlastností** projektu.

2. Klikněte na stránku vlastností **Build (sestavit** ).

3. Upravte vlastnost **target platformy** a pro projekty, které cílí na .NET Framework 4,5 zaškrtněte políčko **preferovat 32-bit** nebo zrušte jeho zaškrtnutí.

> [!NOTE]
> `-platform`není k dispozici ve vývojovém prostředí v C# aplikaci Visual Express.

Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>v tématu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít možnost **-Platform** k určení toho, že by aplikace měla běžet 64 modul CLR na 64 operačním systému Windows.

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
