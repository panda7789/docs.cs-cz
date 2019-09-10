---
title: Kanonické funkce
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: f8ca9e2027e82db89e91287fda02d2014d53f325
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854510"
---
# <a name="canonical-functions"></a>Kanonické funkce
Tato část popisuje kanonické funkce, které jsou podporovány všemi zprostředkovateli dat, a lze je použít všemi technologiemi pro dotazování. Kanonické funkce nelze od poskytovatele rozšířit.  
  
 Tyto kanonické funkce budou přeloženy na odpovídající funkce zdroje dat pro poskytovatele. To umožňuje vyvolání funkcí vyjádřené ve společném formuláři napříč zdroji dat.  
  
 Vzhledem k tomu, že tyto kanonické funkce jsou nezávislé na zdrojích dat, argumenty a návratové typy kanonických funkcí jsou definovány v koncepčním modelu. Některé zdroje dat však nemusí podporovat všechny typy v koncepčním modelu.  
  
 Pokud jsou v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu použity kanonické funkce, příslušná funkce bude volána ve zdroji dat.  
  
 Všechny kanonické funkce mají jak chování vstupu null, tak i chybové stavy, které jsou explicitně určeny. Poskytovatelé úložiště by měli dodržovat toto chování, ale Entity Framework toto chování neuplatní.  
  
 Pro scénáře LINQ dotazy na Entity Framework zahrnují mapování metod CLR na metody v podkladovém zdroji dat. Metody CLR se mapují na kanonické funkce, takže konkrétní sada metod bude správně namapována, bez ohledu na zdroj dat.  
  
## <a name="canonical-functions-namespace"></a>Obor názvů kanonických funkcí  
 Obor názvů pro kanonickou funkci <xref:System.Data.Metadata.Edm>je. <xref:System.Data.Metadata.Edm> Obor názvů je automaticky zahrnutý ve všech dotazech. Pokud je však importován jiný obor názvů, který obsahuje funkci se stejným názvem jako kanonická funkce (v <xref:System.Data.Metadata.Edm> oboru názvů), je nutné zadat obor názvů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Agregační kanonické funkce](aggregate-canonical-functions.md)  
 Popisuje agregační [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Matematické kanonické funkce](math-canonical-functions.md)  
 Popisuje matematické [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Řetězcové kanonické funkce](string-canonical-functions.md)  
 Popisuje řetězcové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Kanonické funkce pro datum a čas](date-and-time-canonical-functions.md)  
 Popisuje kanonické funkce [!INCLUDE[esql](../../../../../../includes/esql-md.md)] data a času.  
  
 [Bitové kanonické funkce](bitwise-canonical-functions.md)  
 Popisuje bitové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Prostorové funkce](spatial-functions.md)  
 Popisuje prostorové [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonické funkce.  
  
 [Jiné kanonické funkce](other-canonical-functions.md)  
 Popisuje funkce, které nejsou klasifikovány jako bitové, datum a čas, řetězec, matematika nebo agregace.  
  
## <a name="see-also"></a>Viz také:

- [Přehled Entity SQL](entity-sql-overview.md)
- [Reference k Entity SQL](entity-sql-reference.md)
- [Konceptuální model v kanonickém formátu pro mapování funkcí SQL Serveru](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [Uživatelem definované funkce](user-defined-functions-entity-sql.md)
