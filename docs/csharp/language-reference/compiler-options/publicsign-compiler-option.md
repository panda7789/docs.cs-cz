---
description: -publicsign (možnosti kompilátoru C#)
title: -publicsign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124809"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (možnosti kompilátoru C#)

Tato možnost způsobí, že kompilátor použije veřejný klíč, ale ve skutečnosti nepodepíše sestavení. Možnost **-publicsign** také nastavuje bitovou kopii v sestavení, která oznamuje modulu runtime, že soubor je skutečně podepsán.

## <a name="syntax"></a>Syntaxe

```console
-publicsign
```

## <a name="arguments"></a>Argumenty

Žádné

## <a name="remarks"></a>Poznámky

Možnost **-publicsign** vyžaduje použití souboru [-keyfile](keyfile-compiler-option.md) nebo [-klíče obsahujícího](keycontainer-compiler-option.md). **Možnosti souboru** **keyfile nebo klíče** určují veřejný klíč.

Možnosti **-publicsign** a **-delaysign** se vzájemně vylučují.

Při veřejném zápisu se někdy označuje jako "falešné znaménko" nebo "znak OSS", ale veřejný podpis zahrnuje veřejný klíč ve výstupním sestavení a nastavuje příznak "signed", ale ve skutečnosti nepodepisuje sestavení pomocí privátního klíče. To je užitečné pro open source projekty, kde lidé chtějí sestavovat sestavení, která jsou kompatibilní s vydanými sestaveními "plně podepsaný", ale nemají přístup k privátnímu klíči, který se používá k podepsání sestavení. Vzhledem k tomu, že téměř žádní spotřebitelé nepotřebují ověřit, jestli je sestavení plně podepsané, tato veřejně vytvořená sestavení jsou použitelná v téměř každém scénáři, kde se používá plně podepsaný certifikát.

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a>Nastavení této možnosti kompilátoru v souboru csproj

Otevřete soubor. csproj pro projekt a přidejte následující element:

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a>Viz také

- [Kompilátor C# – možnost delaysign](delaysign-compiler-option.md)
- [C# – možnost kompilátoru – parametr keyfile](keyfile-compiler-option.md)
- [Kompilátor C# – možnost obsahuje](keycontainer-compiler-option.md)
- [Možnosti kompilátoru C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
