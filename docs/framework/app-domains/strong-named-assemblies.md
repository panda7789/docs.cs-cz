---
title: Sestavení se silným názvem
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 72e9e698e510153073515aa891f1ed3b4d7b9886
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705516"
---
# <a name="strong-named-assemblies"></a>Sestavení se silným názvem
Silné názvy sestavení vytvoří jedinečnou identitu pro sestavení a může zabránit konfliktům při sestavení.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Co vlastně sestavení se silným názvem?  
 Silně pojmenované sestavení je generováno pomocí privátního klíče, který odpovídá veřejnému klíči distribuovat se sestavení a samotného sestavení. Sestavení obsahuje manifest sestavení, který obsahuje názvy a hash hodnoty všech souborů, které tvoří sestavení. Sestavení, která se stejným silným názvem musí být identické.  
  
 Je možné sestavení se silným názvem pomocí sady Visual Studio nebo nástroje příkazového řádku. Další informace najdete v tématu [jak: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) nebo [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Když se vytvoří sestavení se silným názvem, obsahuje jednoduchý textový název sestavení, číslo verze, jazykovou verzi volitelné informace, digitální podpis a veřejný klíč, který odpovídá privátní klíč používaný k podepisování.  
  
> [!WARNING]
>  Nespoléhejte na silných názvů pro zabezpečení. Poskytují jedinečné identity.  
  
## <a name="why-strong-name-your-assemblies"></a>Proč se silným názvem vašeho sestavení?  
 Při odkazování na sestavení se silným názvem, můžete očekávat určité výhody, jako je například Správa verzí a pojmenování ochrany. Sestavení se silným názvem je možné nainstalovat do globální mezipaměti sestavení, je nutná pro povolení některé scénáře.  
  
 Sestavení se silným názvem jsou užitečné v následujících scénářích:  
  
- Chcete povolit vaše sestavení může odkazovat sestavení se silným názvem, nebo chcete poskytnout `friend` přístup k sestavení z jiných sestavení se silným názvem.  
  
- Aplikace potřebuje přístup k různé verze téhož sestavení. To znamená, že potřebujete různé verze sestavení, které chcete načíst vedle sebe ve stejné doméně aplikace bez konfliktu. Například pokud různých rozšíření rozhraní API v sestavení, které mají stejný jednoduchý název, silné názvy poskytuje jedinečné identity pro každou verzi sestavení.  
  
- Nechcete negativně ovlivnit výkon aplikace pomocí sestavení, takže má sestavení jako doménově neutrální. To vyžaduje silné názvy protože doménově neutrální sestavení musí být nainstalováno v globální mezipaměti sestavení.  
  
- Pokud chcete centralizovat údržby pro vaši aplikaci s použitím zásad vydavatele, což znamená, že sestavení v globální mezipaměti sestavení musí nainstalovat.  
  
 Pokud jsou open source vývojářů a chcete využít výhod Identita sestavení se silným názvem, je vhodné zkontrolovat v privátní klíč přidružený k sestavení do systému správy zdrojů.  
  
## <a name="see-also"></a>Viz také:

- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)
- [Postupy: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
