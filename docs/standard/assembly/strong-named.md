---
title: Sestavení se silným názvem
description: Přečtěte si o silných názvech pro sestavení .NET, která vytvoří jedinečnou identitu pro sestavení a může zabránit konfliktům sestavení.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
ms.openlocfilehash: 069e42af6f8d49363d0264c0f6167b4afa3acd61
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925654"
---
# <a name="strong-named-assemblies"></a>Sestavení se silným názvem

Silné pojmenovávání sestavení vytvoří jedinečnou identitu pro sestavení a může zabránit konfliktům sestavení.

## <a name="what-makes-a-strong-named-assembly"></a>Co dělá sestavení se silným názvem?

Silné pojmenované sestavení je generováno pomocí privátního klíče, který odpovídá veřejnému klíči distribuovanému se sestavením a samotným sestavením. Sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, ze kterých se skládá sestavení. Sestavení se stejným silným názvem by měla být shodná.

Sestavení se silným názvem můžete vytvořit pomocí sady Visual Studio nebo nástroje příkazového řádku. Další informace najdete v tématu [Postup: podepsání sestavení silným názvem](sign-strong-name.md) nebo [Sn.exe (Nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md).

Když je vytvořeno sestavení se silným názvem, obsahuje jednoduchý textový název sestavení, číslo verze, volitelné informace o jazykové verzi, digitální podpis a veřejný klíč, který odpovídá privátnímu klíči používanému k podepisování.

> [!WARNING]
> Nespoléhá se na silné názvy zabezpečení. Poskytují pouze jedinečnou identitu.

## <a name="why-strong-name-your-assemblies"></a>Proč je sestavení silným názvem?

Pro .NET Framework sestavení se silným názvem jsou užitečné v následujících scénářích:

- Chcete povolit odkazování na vaše sestavení pomocí sestavení se silným názvem, nebo chcete udělit `friend` přístup k sestavením z jiných sestavení se silným názvem.

- Aplikace potřebuje přístup k různým verzím stejného sestavení. To znamená, že budete potřebovat různé verze sestavení pro zatížení souběžně ve stejné doméně aplikace bez konfliktu. Například pokud různá rozšíření rozhraní API existují v sestaveních se stejným jednoduchým názvem, silné názvy poskytují jedinečnou identitu pro každou verzi sestavení.

- Nechcete negativně ovlivnit výkon aplikací, které používají sestavení, takže chcete, aby bylo sestavení v doméně neutrální. To vyžaduje silné pojmenovávání, protože v globální mezipaměti sestavení (GAC) musí být nainstalována doménově neutrální sestavení.

- Chcete centralizovat obsluhu pro vaši aplikaci pomocí zásad vydavatele, což znamená, že sestavení musí být nainstalováno v globální mezipaměti sestavení (GAC).

Pro .NET Core sestavení se silným názvem neposkytují materiálové výhody.

Pokud jste Open Source vývojář a chcete, aby výhody identity sestavení se silným názvem pro lepší kompatibilitu s .NET Framework, zvažte vrácení privátního klíče přidruženého k sestavení do systému správy zdrojového kódu.

## <a name="see-also"></a>Viz také

- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Postupy: podepsání sestavení silným názvem](sign-strong-name.md)
- [Sn.exe (Nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
