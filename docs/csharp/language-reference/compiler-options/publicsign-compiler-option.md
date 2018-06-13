---
title: -publicsign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: ec25f9c1f2ef943db41bcfa20c8efd1d05866acd
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472852"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (možnosti kompilátoru C#)

Tato možnost způsobí, že kompilátor veřejný klíč použít, ale není ve skutečnosti podepsání sestavení. **- Publicsign** možnost nastaví trochu v sestavení, které modul runtime informuje, že soubor je ve skutečnosti podepsaná.

## <a name="syntax"></a>Syntaxe

```console
-publicsign
```

## <a name="arguments"></a>Arguments

Žádné

## <a name="remarks"></a>Poznámky

**- Publicsign** možnost vyžaduje použití [- keyfile](keyfile-compiler-option.md) nebo [- keycontainer](keycontainer-compiler-option.md). **Keyfile** nebo **keycontainer** možnosti zadejte veřejný klíč.

**- Publicsign** a **- delaysign** možnosti se vzájemně vylučují.

Někdy označuje jako "falešných přihlášení" nebo "Přihlášení OSS", veřejné podepisování obsahuje veřejný klíč ve výstupu sestavení a nastavuje příznak "podepsaný", ale není ve skutečnosti podepsání sestavení s privátním klíčem. To je užitečné pro projekty s otevřeným zdrojem, kde chcete vytvořit sestavení, které jsou kompatibilní s vydaná "plně podepsaný, sestavení, ale nemáte přístup k privátnímu klíči použité k podepsání sestavení osoby. Vzhledem k tomu, že téměř žádné příjemce skutečně potřeba zkontrolovat, pokud je plně podepsáno sestavení, jsou veřejně předdefinované sestavení funkční v téměř každý scénář, kde se použije plně podepsané jeden.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete **vlastnosti** stránky pro projekt.
1. Změnit **zpoždění podepsání** vlastnost.

## <a name="see-also"></a>Viz také
 [-Delaysign – možnost kompilátor jazyka C#](delaysign-compiler-option.md)  
 [-Keyfile – možnost kompilátor jazyka C#](keyfile-compiler-option.md)  
 [-Keycontainer – možnost kompilátor jazyka C#](keycontainer-compiler-option.md)  
 [Možnosti kompilátoru jazyka C#](index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
