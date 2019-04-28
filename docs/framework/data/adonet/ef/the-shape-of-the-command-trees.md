---
title: Tvar stromu příkazů
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 08a67c8d181188cbc14c6f60876a7e26cd6de25a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763981"
---
# <a name="the-shape-of-the-command-trees"></a>Tvar stromu příkazů

Modul generování SQL je zodpovědný za generování back-endu konkrétní dotaz SQL na základě daný vstupní dotaz příkaz stromu výrazu. Tato část popisuje vlastnosti, vlastnosti a struktuře stromu příkazů dotazů.

## <a name="query-command-trees-overview"></a>Přehled stromů příkaz dotazu

Dotaz stromu příkazů je reprezentaci modelu objektu dotazu. Stromy příkazů dotazů mají dva účely:

- Vyjádřit vstupní dotaz, který je zadán proti [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].

- Vyjádřit dotaz výstup, který je uveden na poskytovatele a popisuje dotazu na back-endu.

Dotazování příkazu stromů podporu bohatší sémantiku než SQL:1999 kompatibilní s dotazy, včetně podpory pro práci s vnořené kolekce a typ operace, jako je kontrola, jestli je entita určitého typu nebo filtrování podle typu sady.

Vlastnost DBQueryCommandTree.Query je kořenem stromu výrazů, který popisuje logiku dotazu. Vlastnost DBQueryCommandTree.Parameters obsahuje seznam parametrů, které se používají v dotazu. Strom výrazu se skládá z DbExpression objekty.

Objekt DbExpression představuje některé výpočtu. Jsou k dispozici v několika druhů výrazy [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pro sestavení výrazy dotazu, včetně konstant, proměnné, funkce, konstruktory a standardní relační operátory, jako je filtrování a spojení. Každý objekt DbExpression má vlastnost ResultType, který představuje typ výsledku vytvořeného tento výraz. Tento typ je vyjádřen jako vlastnost TypeUsage.

## <a name="shapes-of-the-output-query-command-tree"></a>Tvary stromu příkazů výstup dotazu

Stromy příkazů výstup dotazu představují relačních dotazů (SQL) a dodržovat pravidla mnohem větší než ty, které se vztahují na stromy příkaz dotazu. Obvykle obsahují konstrukce, které jsou snadno do kódu SQL.

Vstupní příkaz stromové struktury jsou vyjádřeny proti konceptuální model, který podporuje navigačních vlastností asociace mezi entitami a dědičnost. Výstup příkazu stromů jsou vyjádřeny pro model úložiště. Vstupní příkaz stromů umožňují vnořené kolekce projektů, ale výstup příkazu stromů tomu tak není.

Stromy příkazů výstup dotazu jsou sestaveny na základě podmnožinu dostupných objektů DbExpression a dokonce i některé výrazy v ní mají omezený využití.

Typ operace, jako je kontrola, zda je daný výraz určitého typu nebo filtrování sady na základě typu, nejsou zadány ve výstupu příkazu stromu.

Ve výstupu příkazu stromu se používají pouze výrazy, které vracejí logické hodnoty pro projekce a pouze pro predikáty ve výrazech vyžadující predikátu, jako je filtr nebo příkazy case.

Kořenové stromů příkazů výstup dotazu je objekt DbProjectExpression.

### <a name="expression-types-not-present-in-output-query-command-trees"></a>Typy výrazů není k dispozici v stromů příkazů výstup dotazu

Následující typy výrazů nejsou platné ve výstupu stromu příkaz dotazu a není nutné ošetřit zprostředkovatelé:

- Objekt DbDerefExpression

- DbEntityRefExpression

- Třída DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>Výraz omezení a poznámky

Mnoho výrazů jde použít jenom s omezeným přístupem způsobem v stromů příkazů výstup dotazu:

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

Je možné předat následující typy funkcí:

- Kanonické funkce, které jsou rozpoznány modulem pro obor názvů Edm.

- Funkce integrované (úložiště), které jsou rozpoznány modulem BuiltInAttribute.

- Uživatelem definované funkce.

Kanonické funkce (naleznete v tématu [kanonické funkce](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Další informace) jsou určené jako součást [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], a poskytovatelé by mělo nabízet implementace pro kanonické funkce na základě těchto specifikací. Funkce Store jsou založeny na specifikacích v manifestu zprostředkovatele, odpovídající. Uživatelem definované funkce jsou založeny na specifikacích SSDL.

Funkce s atributem NiladicFunction také nemají žádné argumenty a bez závorky na konci by měl přeložit.  To znamená do  *\<functionName >* místo  *\<functionName > ()*.

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

DbNewInstanceExpression může vyskytovat jenom v těchto dvou případů:

- Jako vlastnost projekce DbProjectExpression.  Pokud se použije jako takové platí následující omezení:

  - Typ výsledku musí být typu řádku.

  - Každá z jejích argumentů je výraz, který vytváří výsledek s primitivního typu. Obvykle každý argument je skalární výraz, stejně jako PropertyExpression DbVariableReferenceExpression, volání funkce nebo pro aritmetické výpočtu DbPropertyExpression přes DbVariableReferenceExpression nebo volání funkce . Ale představující poddotaz skalární výraz může vzniknout také v seznamu argumentů DbNewInstanceExpression. Strom výrazů, který představuje poddotazu, která vrací přesně jeden řádek a jeden sloupec primitivní typ objektu kořenovou DbElementExpression je výraz, který reprezentuje skalární poddotazu

- S návratovým typem kolekce v takovém případě definuje novou kolekci výrazů zadané jako argumenty.

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

DbVariableReferenceExpression musí být podřízeným uzlem DbPropertyExpression uzlu.

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

Vlastnost agregace Dbgroupaggregate může obsahovat pouze prvky typu DbFunctionAggregate. Nejsou žádné další typy agregátů.

#### <a name="dblimitexpression"></a>DbLimitExpression

Vlastnost Limit může být pouze objekt DbConstantExpression nebo DbParameterReferenceExpression. Také vlastnost WithTies má vždy hodnotu false od verze rozhraní .NET Framework verze 3.5.

#### <a name="dbscanexpression"></a>DbScanExpression

Při použití ve výstupu příkazu stromu, DbScanExpression efektivně představuje kontrolu nad tabulky, zobrazení nebo dotaz úložiště, reprezentovaný EntitySetBase::Target.

Pokud vlastnost metadat "Definice dotazu" cíle je jiná než null, pak představuje dotaz, text dotazu, pro který je součástí této vlastnosti metadat v poskytovatele konkrétní jazyk (nebo dialekt), jak je uvedeno v definici schématu úložiště.

V opačném případě cíl představuje tabulku nebo zobrazení. Jeho předpona schématu je buď ve vlastnosti metadat "Schéma", pokud není null, jinak je název kontejneru entity.  Název tabulky nebo zobrazení je buď vlastnost metadat "Table", pokud není null, jinak nastavte základní vlastnosti název entity.

Všechny tyto vlastnosti pocházejí z definice odpovídající objekt EntitySet v souboru definice schématu úložiště (SSDL).

### <a name="using-primitive-types"></a>Primitivní typy

Pokud se ve výstupu příkazu stromů odkazuje primitivní typy, jsou obvykle odkazovány v primitivních typech Koncepční model. Pro některé výrazy musí poskytovatelé primitivní typ odpovídající úložiště. Tyto výrazy příklady DbCastExpression a případně DbNullExpression, pokud zprostředkovatel potřebuje k přetypování hodnoty null na typ odpovídající. V těchto případech poskytovatelů proveďte mapování na základě typ primitivní typ a její omezující vlastnosti typu zprostředkovatele rozhraní.

## <a name="see-also"></a>Viz také:

- [Generování SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
