---
title: -platforma (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 5150e871d75c3c34dab10f10cdac3d8322d7a834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70849877"
---
# <a name="-platform-c-compiler-options"></a>-platforma (Možnosti kompilátoru Jazyka C#)

Určuje, která verze clr (Common Language Runtime) může spustit sestavení.

## <a name="syntax"></a>Syntaxe

```console
-platform:string
```

## <a name="parameters"></a>Parametry

`string` \
anycpu (výchozí), anycpu32bitpreferred, ARM, x64, x86 nebo Itanium.

## <a name="remarks"></a>Poznámky

- **anycpu** (výchozí) zkompiluje sestavení spustit na libovolné platformě. Aplikace běží jako 64bitový proces, kdykoli je to možné, a přejde zpět na 32bitový, pokud je k dispozici pouze tento režim.

- **anycpu32bitpreferred** zkompiluje sestavení spustit na libovolné platformě. Aplikace běží v 32bitovém režimu v systémech, které podporují 64bitové i 32bitové aplikace. Tuto možnost můžete zadat pouze pro projekty, které cílí na rozhraní .NET Framework 4.5.

- **ARM** zkompiluje sestavení ke spuštění v počítači, který má procesor Advanced RISC Machine (ARM).

- **ARM64** zkompiluje sestavení ke spuštění 64bitové CLR v počítači, který má procesor Advanced RISC Machine (ARM), který podporuje instrukční sadu A64.

- **x64** zkompiluje sestavení, které má být spuštěno 64bitovým clr v počítači, který podporuje instrukční sadu AMD64 nebo EM64T.

- **x86** zkompiluje sestavení, které bude spuštěno 32bitovým kódem CLR kompatibilním s x86.

- **Itanium** zkompiluje sestavení, které bude spuštěno 64bitovým CLR v počítači s procesorem Itanium.

V 64bitovém operačním systému Windows:

- Sestavení zkompilovaná s **-platform:x86** se provádějí na 32bitovém CLR běžícím pod WOW64.

- DLL zkompilované s **-platform:anycpu** spustí na stejném CLR jako proces, do kterého je načten.

- Spustitelné soubory, které jsou kompilovány s **-platform:anycpu** spustit na 64bitclr.

- Spustitelné soubory zkompilované s **-platform:anycpu32bitpreferred** provést na 32bitCLR.

**Anycpu32bitpreferred** nastavení je platné pouze pro spustitelný soubor (. EXE) a vyžaduje rozhraní .NET Framework 4.5.

Další informace o vývoji aplikace pro spuštění v 64bitovém operačním systému Windows naleznete v [64bitových aplikacích](../../../framework/64-bit-apps.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete stránku **Vlastnosti** projektu.

2. Klikněte na stránku vlastností **Sestavení.**

3. Upravte vlastnost **Target platformy** a u projektů, které cílí na rozhraní .NET Framework 4.5, zaškrtněte nebo zrušte zaškrtnutí políčka **Preferovat 32bitový.**

> [!NOTE]
> `-platform`není k dispozici ve vývojovém prostředí v jazyce Visual C# Express.

Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>kompilátoru programově, naleznete v tématu .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak pomocí **-platforma** možnost určit, že aplikace by měla být spuštěna 64bitový CLR na 64bitový operační systém Windows.

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
