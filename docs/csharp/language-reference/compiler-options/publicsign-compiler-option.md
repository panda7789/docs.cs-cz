---
title: -publicsign (C# Možnosti kompilátoru)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662527"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (C# Možnosti kompilátoru)

Tato možnost způsobí, že kompilátor použít veřejný klíč, ale ve skutečnosti nepodepisuje sestavení. Možnost **-publicsign** také nastaví bit v sestavení, který říká, že soubor je skutečně podepsán.

## <a name="syntax"></a>Syntaxe

```console
-publicsign
```

## <a name="arguments"></a>Argumenty

Žádné.

## <a name="remarks"></a>Poznámky

Možnost **-publicsign** vyžaduje použití [-keyfile](keyfile-compiler-option.md) nebo [-keycontainer](keycontainer-compiler-option.md). Možnosti **keyfile** nebo **keycontainer** určují veřejný klíč.

Možnosti **-publicsign** a **-delaysign** se vzájemně vylučují.

Někdy se nazývá "falešné znamení" nebo "znak OSS", veřejné podepisování zahrnuje veřejný klíč ve výstupním sestavení a nastaví příznak "podepsáno", ale ve skutečnosti nepodepisuje sestavení pomocí soukromého klíče. To je užitečné pro projekty s otevřeným zdrojovým kódem, kde uživatelé chtějí vytvářet sestavení, která jsou kompatibilní s vydanými "plně podepsanými" sestaveními, ale nemají přístup k soukromému klíči používanému k podepisování sestavení. Vzhledem k tomu, že téměř žádní spotřebitelé skutečně potřebují zkontrolovat, zda je sestavení plně podepsáno, jsou tato veřejně vytvořená sestavení použitelná téměř ve všech scénářích, kde by bylo použito plně podepsané sestavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete stránku **Vlastnosti** projektu.
1. Upravte pouze vlastnost **znaménko Zpoždění.**

## <a name="see-also"></a>Viz také

- [C# Compiler -delaysign, volba](delaysign-compiler-option.md)
- [C# Kompilátor -keyfile, volba](keyfile-compiler-option.md)
- [C# Kompilátor -keycontainer, možnost](keycontainer-compiler-option.md)
- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
