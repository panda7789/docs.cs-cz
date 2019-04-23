---
title: Kanonické funkce
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 380c1dbcf86d8bbb844c2b226697d72d00c3e81a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202934"
---
# <a name="canonical-functions"></a>Kanonické funkce
Tato část popisuje kanonické funkce, které jsou podporovány všechny poskytovatele dat a může využívat všechny dotazy technologie. Kanonické funkce nelze rozšířit poskytovatelem.  
  
 Tyto kanonické funkce se přeložit na funkci odpovídající zdroj dat poskytovatele. To umožňuje vyjádřené v běžné formě napříč zdroji dat obsahující záznamy volání funkcí.  
  
 Protože tyto kanonické funkce jsou nezávislé na zdroje dat, jsou definována v argumentu a návratovým typem kanonické funkce typů v konceptuálním modelu. Některé zdroje dat však nemusí podporovat všechny typy v konceptuálním modelu.  
  
 Při použití kanonické funkce v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu, příslušnou funkci bude volána ve zdroji dat.  
  
 Všechny kanonické funkce mají chování vstupní hodnotu null a chybové stavy explicitně zadán. Poskytovatelé Store by měly splňovat toto chování ale [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nevynucuje toto chování.  
  
 U scénářů s LINQ dotazy proti [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] zahrnují mapování metod v podkladovém zdroji dat metod modulu CLR. Mapu metod modulu CLR, aby kanonické funkce tak, aby konkrétní sadu metod se správně rozvržení, bez ohledu na zdroj dat  
  
## <a name="canonical-functions-namespace"></a>Namespace kanonické funkce  
 Obor názvů pro kanonické funkce je <xref:System.Data.Metadata.Edm>. <xref:System.Data.Metadata.Edm> Obor názvů je automaticky zahrnut ve všech dotazů. Ale pokud dojde k importu jiný obor názvů, který obsahuje funkce se stejným názvem jako kanonické funkce (v <xref:System.Data.Metadata.Edm> oboru názvů), je nutné zadat obor názvů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Agregační kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 Tento článek popisuje agregace [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Matematické kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 Tento článek popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Řetězcové kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 Tento článek popisuje řetězec [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Kanonické funkce pro datum a čas](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 Tento článek popisuje data a času [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Bitové kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 Tento článek popisuje bitový [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Prostorové funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 Tento článek popisuje Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Jiné kanonické funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 Tento článek popisuje funkce nejsou klasifikovány jako bitové operace, datum a čas, řetězec, matematických výpočtů nebo agregace.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [Uživatelem definované funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
