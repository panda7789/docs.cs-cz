---
title: Sestavení se silným názvem
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7cbef005c913d818dba23d85404fe0382fe79f4a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="strong-named-assemblies"></a>Sestavení se silným názvem
Silné názvy sestavení vytvoří jedinečnou identitu pro sestavení a může zabránit konfliktům sestavení.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Díky sestavení se silným názvem?  
 Silně pojmenované sestavení je generována pomocí privátního klíče, který odpovídá veřejnému klíči distribuované s sestavení a sestavení sám sebe. Sestavení obsahuje manifest sestavení, který obsahuje názvy a hodnoty hash všech souborů, které tvoří sestavení. Sestavení, které mají stejný název silné musí být identické.  
  
 Sestavení se silným názvem můžete pomocí sady Visual Studio nebo nástroj příkazového řádku. Další informace najdete v tématu [postupy: podepsání sestavení se silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) nebo [Sn.exe (nástroj silným názvem)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Při vytváření sestavení se silným názvem, obsahuje jednoduchý textový název sestavení, číslo verze, informace o jazykové verzi volitelné, digitální podpis a veřejný klíč, který odpovídá privátní klíč použít pro podepisování.  
  
> [!WARNING]
>  Nespoléhejte na silné názvy pro zabezpečení. Obsahují jenom jedinečnou identitu.  
  
## <a name="why-strong-name-your-assemblies"></a>Proč se silným názvem vaší sestavení?  
 Když odkazujete na sestavení se silným názvem, můžete očekávat určité výhody, jako je například Správa verzí a pojmenování ochrany. Sestavení se silným názvem lze nainstalovat do globální mezipaměti sestavení, které je potřeba povolit některé scénáře.  
  
 Sestavení se silným názvem jsou užitečné v následujících scénářích:  
  
-   Chcete povolit vaše sestavení, které může být odkazuje sestavení se silným názvem, nebo chcete poskytnout `friend` přístup k vaší sestavení od ostatních sestavení se silným názvem.  
  
-   Aplikace potřebuje přístup pro různé verze stejného sestavení. To znamená, že potřebujete různé verze sestavení načíst vedle sebe ve stejné doméně aplikace bez konfliktů. Například pokud je v sestavení, které mají stejný jednoduchý název různých rozšíření rozhraní API, silné názvy poskytuje jedinečnou identitu pro každou verzi sestavení.  
  
-   Nechcete negativně ovlivnit výkon aplikace sestavení, takže chcete sestavení do domény neutrální. To vyžaduje silné názvy protože domény jazykově neutrální sestavení v globální mezipaměti sestavení musí být nainstalován.  
  
-   Pokud chcete centralizovat údržby pro vaši aplikaci s použitím zásad vydavatele, což znamená, že sestavení v globální mezipaměti sestavení musí nainstalovat.  
  
 Pokud jste vývojář open source a chcete využít výhod identity sestavení se silným názvem, zvažte kontrolu v privátní klíč přidružený k sestavení do systému správy zdrojů.  
  
## <a name="see-also"></a>Viz také  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Postupy: Podepsání sestavení silným názvem](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
