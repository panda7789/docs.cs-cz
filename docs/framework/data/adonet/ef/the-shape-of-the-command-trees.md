---
title: Obrazec stromy příkazů
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 9084e2616ac4ea540bdf755afd011d67a5c991fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="the-shape-of-the-command-trees"></a>Obrazec stromy příkazů
Modul generování SQL je zodpovědný za generování back-end konkrétní dotaz SQL na základě výrazu stromu příkaz daný vstupní dotaz. Tato část popisuje vlastnosti, vlastnosti a struktura stromy příkazů dotazu.  
  
## <a name="query-command-trees-overview"></a>Přehled stromy příkaz dotazu  
 Dotaz stromu příkazů je reprezentaci objektu modelu dotazu. Dotazů stromy příkazů mají dva účely:  
  
-   Vyjádřit vstupní dotaz, který je zadaný na [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Chcete-li express dotazu výstup, který je uveden na poskytovatele a popisuje dotazy na back-end.  
  
 Dotaz příkaz podporu stromy bohatší sémantiku než SQL:1999 kompatibilní dotazů, včetně podpory pro práci s vnořené kolekce a typ operací, jako je kontrola, zda je entita určitého typu nebo filtrování sady založený na typu.  
  
 Vlastnost DBQueryCommandTree.Query je kořenem strom výrazu, která popisuje logiku dotazu. Vlastnost DBQueryCommandTree.Parameters obsahuje seznam parametrů, které se používají v dotazu. Strom výrazu se skládá z objekty od objektu DbExpression.  
  
 Objekt DbExpression představuje některé výpočty. Několik druhů výrazy jsou poskytovány [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro sestavování výrazy dotazů, včetně konstanty, proměnné, funkce, konstruktory a standardní relační operátory jako filtr a připojení. Každý objekt DbExpression má hodnotu ResultType vlastnost, která představuje typ výsledku vytvořeného tento výraz. Tento typ je vyjádřen jako TypeUsage.  
  
## <a name="shapes-of-the-output-query-command-tree"></a>Tvary strom příkazů výstup dotazu  
 Stromy příkazů dotazu výstup úzce představují relační dotazy (SQL) a splňovat pravidla mnohem přísnější než ty, které platí pro dotazů stromy příkazů. Obvykle obsahují konstrukce, které jsou snadno převedeny na SQL.  
  
 Vstupní příkaz stromy jsou vyjádřeny proti konceptuální model, který podporuje navigační vlastnosti přidružení mezi entitami a dědičnost. Výstup příkazu stromy jsou vyjádřeny pro model úložiště. Zadejte stromy příkazů umožňují projektu vnořené kolekce, ale nechcete stromy příkazů výstup.  
  
 Stromy příkazů výstup dotazu jsou vytvořeny pomocí podmnožinu dostupných objektů DbExpression a i některé výrazy v tuto podmnožinu mají omezený využití.  
  
 Typ operace, jako je kontrola, zda je daný výraz určitého typu nebo filtrování podle typu, nastaví se nenacházejí v výstup stromy příkazů.  
  
 Ve výstupu příkazu stromy používají pouze výrazy, které vracejí logické hodnoty pro projekce a pouze pro predikáty ve výrazech nutnosti predikátu, jako je filtr nebo příkaz case.  
  
 Kořenové stromy příkazů výstupu dotazu je objekt DbProjectExpression.  
  
### <a name="expression-types-not-present-in-output-query-command-trees"></a>Typy výrazů není k dispozici v stromy příkazů výstup dotazu  
 Následující typy výrazů nejsou platné ve stromu příkazů výstupu dotazu a není potřeba ji zpracovat zprostředkovatele:  
  
 Objekt DbDerefExpression  
  
 Třída DbEntityRefExpression  
  
 Třída DbRefKeyExpression  
  
 DbIsOfExpression  
  
 DbOfTypeExpression  
  
 DbRefExpression  
  
 DbRelationshipNavigationExpression  
  
 DbTreatExpression  
  
### <a name="expression-restrictions-and-notes"></a>Výraz omezení a poznámky  
 Mnoho výrazů lze použít pouze s omezeným přístupem způsobem v stromy příkazů výstup dotazu:  
  
#### <a name="dbfunctionexpression"></a>DbFunctionExpression  
 Následující typy funkce se dá předat:  
  
-   Kanonické funkce, které jsou rozpoznány podle oboru názvů Edm.  
  
-   Funkce integrované (úložiště), které rozpoznává BuiltInAttribute.  
  
-   Uživatelem definované funkce.  
  
 Kanonické funkce (najdete v části [kanonické funkce](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) informace) jsou určené jako součást [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], a poskytovatelé měli zadat implementace pro kanonické funkce na základě těchto specifikací. Funkce úložiště jsou založená na specifikacích v manifestu zprostředkovatele, odpovídající. Uživatelem definované funkce jsou založená na specifikacích v SSDL.  
  
 Také funkce s atribut NiladicFunction nemají žádné argumenty a by měl přeložit bez závorek na konci.  To znamená, do  *\<%{FunctionName/ >* místo  *\<%{FunctionName/ > ()*.  
  
#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression  
 DbNewInstanceExpression může dojít pouze v těchto dvou případů:  
  
-   Jako vlastnost projekce DbProjectExpression.  Pokud se používá jako takový platí následující omezení:  
  
    -   Výsledný typ musí být typ řádku.  
  
    -   Každá jeho argumentů je výraz, který vytvoří výsledek s primitivního typu. Obvykle je každý argument skalární výraz, jako je PropertyExpression přes DbVariableReferenceExpression, volání funkce nebo aritmetické výpočet DbPropertyExpression přes DbVariableReferenceExpression nebo volání funkce . Výraz představující skalární poddotazu může také dojít v seznamu argumentů DbNewInstanceExpression. Výraz, který reprezentuje skalární poddotazu je představující poddotaz, který vrátí přesně jeden řádek a jeden sloupec s kořenové objekt DbElementExperession primitivního typu strom výrazu  
  
-   S návratovým typem kolekce v takovém případě definuje novou kolekci výrazů zadané jako argumenty.  
  
#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 DbVariableReferenceExpression musí být podřízenou DbPropertyExpression uzlu.  
  
#### <a name="dbgroupbyexpression"></a>DbGroupByExpression  
 Vlastnost agregací pro DbGroupByExpression může mít pouze elementy typu DbFunctionAggregate. Nejsou žádné jiné agregované typy.  
  
#### <a name="dblimitexpression"></a>DbLimitExpression  
 Vlastnost omezení lze pouze objekt DbConstantExpression nebo DbParameterReferenceExpression. Také vlastnost WithTies je vždy false od verze rozhraní .NET Framework verze 3.5.  
  
#### <a name="dbscanexpression"></a>DbScanExpression  
 Při použití ve výstupu příkazu stromy, DbScanExpression efektivně představuje kontrolu nad tabulky, zobrazení nebo dotaz úložiště, reprezentována EnitySetBase::Target.  
  
 Pokud vlastnost metadat "Definování dotaz" cíle jinou hodnotu než null, reprezentuje dotazu, text dotazu, pro který je součástí tuto vlastnost metadata v konkrétní jazyk poskytovatele (nebo dialektu) jako zadaný v definici schématu úložiště.  
  
 Cíl, jinak hodnota představuje tabulku nebo zobrazení. Předponu jeho schématu je buď ve vlastnosti metadat "Schématu", pokud nejsou null, jinak je název kontejneru entit.  Název tabulky nebo zobrazení je buď vlastnost metadat "Tabulka", pokud nejsou null, jinak hodnota nastavený základní vlastnost název entity.  
  
 Tyto vlastnosti pocházejí z definice odpovídající EntitySet v souboru definice schéma úložiště (SSDL).  
  
### <a name="using-primitive-types"></a>Pomocí primitivní typy  
 Když jsou ve výstupu příkazu stromech primitivní typy, jsou obvykle odkazovat v primitivních typech konceptuální model. Pro určité výrazy potřebovat zprostředkovatelé primitivní typ odpovídající úložiště. Tyto příklady výrazů DbCastExpression a případně DbNullExpression, pokud je potřeba převést hodnotu null na odpovídající typ poskytovatele. V těchto případech by měl zprostředkovatelé udělat mapování, aby na základě typu primitivní typ a jeho omezující vlastnosti typu poskytovatele.  
  
## <a name="see-also"></a>Viz také  
 [Generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
