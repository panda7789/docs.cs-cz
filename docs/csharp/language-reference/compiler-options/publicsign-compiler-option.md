---
title: -publicsign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 01ce30b9ac5997f56f29dcbbfa43a27738fa5556
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184980"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (možnosti kompilátoru C#)

Tato možnost způsobí, že kompilátor použít veřejný klíč, ale není ve skutečnosti podepsat sestavení. **- Publicsign** možnost nastaví bit v sestavení, že modul runtime, že soubor je ve skutečnosti podepsán.

## <a name="syntax"></a>Syntaxe

```console
-publicsign
```

## <a name="arguments"></a>Arguments

Žádné

## <a name="remarks"></a>Poznámky

**- Publicsign** možnost vyžaduje použití [- keyfile](keyfile-compiler-option.md) nebo [- keycontainer](keycontainer-compiler-option.md). **Keyfile** nebo **keycontainer** možnosti zadat veřejný klíč.

**- Publicsign** a **- delaysign** možnosti se vzájemně vylučují.

Někdy označuje jako "falešnou přihlášení" nebo "OSS znak", veřejné podepisování obsahuje veřejný klíč v sestavení výstupu a nastaví příznak "podepsaný", ale není ve skutečnosti podepsat sestavení s privátním klíčem. To je užitečné pro open source projekty, pokud chtějí uživatelé vytvářet sestavení, které jsou kompatibilní s vydaných sestavení "plně podepsané", ale nemají přístup k privátnímu klíči použitý k podepsání sestavení. Protože téměř žádné příjemce ve skutečnosti je potřeba zkontrolovat, pokud je plně podepsané sestavení, předdefinované veřejně sestavení jsou použitelných téměř každý scénář, ve kterém se použije plně podepsané jeden.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřít **vlastnosti** stránky pro projekt.
1. Upravit **zpoždění podepsání** vlastnost.

## <a name="see-also"></a>Viz také

- [-Delaysign – možnost kompilátoru jazyka C#](delaysign-compiler-option.md)  
- [-Keyfile – možnost kompilátoru jazyka C#](keyfile-compiler-option.md)  
- [-Keycontainer – možnost kompilátoru jazyka C#](keycontainer-compiler-option.md)  
- [Možnosti kompilátoru jazyka C#](index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
