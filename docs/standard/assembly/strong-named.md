---
title: Sestavení se silným názvem
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
ms.openlocfilehash: 12b8df3195b2708e4556d4f8065227054db9eb14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711568"
---
# <a name="strong-named-assemblies"></a>Sestavení se silným názvem

Silné pojmenování sestavení vytvoří jedinečnou identitu pro sestavení a může zabránit konfliktům sestavení.

## <a name="what-makes-a-strong-named-assembly"></a>Co dělá sestavení se silným názvem?

Silné pojmenované sestavení je generováno pomocí soukromého klíče, který odpovídá veřejnému klíči distribuovanému se sestavením a samotnému sestavení. Sestavení obsahuje manifest sestavení, který obsahuje názvy a hashy všech souborů, které tvoří sestavení. Sestavení, která mají stejný silný název, by měla být identická.

Sestavení silných názvů můžete použít pomocí sady Visual Studio nebo nástroje příkazového řádku. Další informace naleznete v [tématu Jak: Podepsání sestavení silným názvem](sign-strong-name.md) nebo [Sn.exe (nástroj silný název).](../../framework/tools/sn-exe-strong-name-tool.md)

Při vytvoření sestavení se silným názvem obsahuje jednoduchý textový název sestavení, číslo verze, volitelné informace o jazykové verzi, digitální podpis a veřejný klíč, který odpovídá soukromému klíči používanému k podepisování.

> [!WARNING]
> Nespoléhejte se na silné názvy pro zabezpečení. Poskytují pouze jedinečnou identitu.

## <a name="why-strong-name-your-assemblies"></a>Proč silné jméno sestavení?

Když odkazujete na sestavení se silným názvem, můžete očekávat určité výhody, jako je například správa verzí a ochrana před pojmenováním. V rozhraní .NET Framework lze sestavení se silným názvem nainstalovat do globální mezipaměti sestavení, což je nutné k povolení některých scénářů.

Sestavení se silným názvem jsou užitečná v následujících scénářích:

- Chcete povolit sestavení, která mají být odkazována sestaveními se `friend` silným názvem, nebo chcete udělit přístup k sestavením z jiných sestavení se silným názvem.

- Aplikace potřebuje přístup k různým verzím stejného sestavení. To znamená, že potřebujete různé verze sestavení k načtení vedle sebe ve stejné doméně aplikace bez konfliktu. Například pokud existují různá rozšíření rozhraní API v sestaveních, které mají stejný jednoduchý název, silné pojmenování poskytuje jedinečnou identitu pro každou verzi sestavení.

- Nechcete negativně ovlivnit výkon aplikací pomocí sestavení, takže chcete, aby sestavení bylo neutrální z domény. To vyžaduje silné pojmenování, protože doálně neutrální sestavení musí být nainstalováno v globální mezipaměti sestavení.

- Chcete centralizovat obsluhu aplikace použitím zásad vydavatele, což znamená, že sestavení musí být nainstalováno v globální mezipaměti sestavení.

Pokud jste vývojář s otevřeným zdrojovým kódem a chcete výhody identity sestavení se silným názvem, zvažte vrácení soukromého klíče přidruženého k sestavení do systému správy zdrojového kódu.

## <a name="see-also"></a>Viz také

- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Postup: Podepsání sestavení se silným názvem](sign-strong-name.md)
- [Sn.exe (nástroj silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
