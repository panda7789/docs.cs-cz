---
title: Tvar stromu příkazů
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: a3568f3deeaeeb31b69b41ac7c767001b792a8eb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248225"
---
# <a name="the-shape-of-the-command-trees"></a>Tvar stromu příkazů

Modul SQL Generation je zodpovědný za generování dotazu SQL specifického pro back-end založeného na daném vstupním výrazu příkazu dotazu. Tato část popisuje vlastnosti, vlastnosti a strukturu stromů příkazů dotazu.

## <a name="query-command-trees-overview"></a>Přehled stromů příkazů dotazů

Strom příkazů dotazu je reprezentace objektového modelu dotazu. Stromy příkazů dotazu slouží dvěma účelům:

- Pro vyjádření vstupního dotazu, který je určen [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]pro.

- Aby bylo možné vyjádřit výstupní dotaz, který je dán poskytovateli, a popisuje dotaz na back-end.

Stromy příkazů dotazů podporují bohatší sémantiku než dotazy kompatibilní s SQL: 1999, včetně podpory pro práci s vnořenými kolekcemi a operacemi typu, jako je například kontrola, zda entita je určitého typu, nebo filtrování sad založených na typu.

Vlastnost DBQueryCommandTree. Query je kořenem stromu výrazu, který popisuje logiku dotazu. Vlastnost DBQueryCommandTree. Parameters obsahuje seznam parametrů, které se používají v dotazu. Strom výrazu se skládá z objektů DbExpression.

Objekt DbExpression představuje některé výpočty. K dispozici je [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] několik druhů výrazů pro vytváření výrazů pro dotaz, včetně konstant, proměnných, funkcí, konstruktorů a standardních relačních operátorů, jako je filtr a spojení. Každý objekt DbExpression má vlastnost ResultType, která představuje typ výsledku vytvořeného tímto výrazem. Tento typ je vyjádřený jako TypeUsage.

## <a name="shapes-of-the-output-query-command-tree"></a>Tvary stromu příkazů pro výstupní dotaz

Ve stromech příkazů pro výstupní dotazy se těsně reprezentují relační dotazy (SQL) a dodržují se mnohem přísnějších pravidel, než jsou ta, která se vztahují na stromy příkazů dotazů. Obvykle obsahují konstrukce, které jsou snadno přeloženy do jazyka SQL.

Stromy vstupních příkazů jsou vyjádřeny na koncepčním modelu, který podporuje navigační vlastnosti, asociace mezi entitami a dědičnost. Stromy příkazů výstupu jsou vyjádřeny na model úložiště. Vstupní stromy příkazů umožňují projektovat vnořené kolekce, ale výstupní stromy příkazů ne.

Stromy příkazů pro výstupní dotazy jsou sestaveny pomocí podmnožiny dostupných objektů DbExpression a dokonce i některých výrazů v této podmnožině mají omezené využití.

Operace typu, jako je například kontrola, zda je daný výraz z konkrétního typu nebo sady filtrování založené na typu, nejsou přítomny ve stromových příkazech výstupu.

Ve stromových větvích příkazů jsou pro projekce použity pouze výrazy, které vracejí logické hodnoty, a pouze pro predikáty ve výrazech vyžadujících predikát, jako je filtr nebo příkaz Case.

Kořen stromů příkazů pro výstupní dotaz je objekt DbProjectExpression.

### <a name="expression-types-not-present-in-output-query-command-trees"></a>Ve stromech příkazů pro výstupní dotazy nejsou k dispozici typy výrazů.

Následující typy výrazů nejsou platné ve stromu příkazů výstupního dotazu a nemusíte je zpracovávat poskytovateli:

- DbDerefExpression

- DbEntityRefExpression

- DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>Omezení výrazů a poznámky

Mnoho výrazů lze použít pouze ve stromových strukturách příkazů pro výstup dotazování v omezeném počtu:

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

Lze předat následující typy funkcí:

- Kanonické funkce, které jsou rozpoznávány oborem názvů EDM.

- Integrované funkce (úložiště), které jsou rozpoznávány BuiltInAttribute.

- Uživatelsky definované funkce.

Kanonické funkce (viz [kanonické funkce](./language-reference/canonical-functions.md) pro další informace) jsou určeny jako součást [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]a poskytovatelé by měli poskytovat implementace pro kanonické funkce na základě těchto specifikací. Funkce úložiště jsou založeny na specifikacích v příslušném manifestu zprostředkovatele. Uživatelsky definované funkce jsou založeny na specifikacích ve SSDL.

Také funkce s atributem NiladicFunction nemají žádné argumenty a měly by být přeloženy bez závorek na konci.  To znamená pro  *\<funkci*  *\<> místo funkce > ()* .

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

DbNewInstanceExpression může probíhat pouze v následujících dvou případech:

- Jako vlastnost projekce DbProjectExpression.  Při použití následujících omezení platí:

  - Výsledný typ musí být typ řádku.

  - Každý z jeho argumentů je výraz, který vytváří výsledek s primitivním typem. Každý argument je typicky skalární výraz, jako je například PropertyExpression přes DbVariableReferenceExpression, vyvolání funkce nebo aritmetický výpočet DbPropertyExpressiony prostřednictvím DbVariableReferenceExpression nebo vyvolání funkce. . Výraz reprezentující skalární poddotaz ale může také nastat v seznamu argumentů pro DbNewInstanceExpression. Výraz reprezentující skalární poddotaz je strom výrazů, který představuje poddotaz, který vrací přesně jeden řádek a jeden sloupec primitivního typu s kořenem objektu DbElementExpression.

- S typem vrácené kolekce, v takovém případě definuje novou kolekci výrazů poskytovaných jako argumenty.

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

DbVariableReferenceExpression musí být podřízeným uzlem uzlu DbPropertyExpression.

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

Vlastnost Aggregates třídy DbGroupAggregate může mít pouze elementy typu DbFunctionAggregate. Neexistují žádné další agregované typy.

#### <a name="dblimitexpression"></a>DbLimitExpression

Omezení vlastnosti může být pouze DbConstantExpression nebo DbParameterReferenceExpression. Vlastnost WithTies je také vždy false jako verze 3,5 .NET Framework.

#### <a name="dbscanexpression"></a>DbScanExpression

Při použití ve výstupních stromových příkazech představuje DbScanExpression efektivně kontrolu nad tabulkou, zobrazením nebo dotazem úložiště, reprezentovaným EntitySetBase:: Target.

Pokud vlastnost metadat "definující dotaz" cílového typu není null, představuje dotaz, který je k dispozici v dané vlastnosti metadat v konkrétním jazyku poskytovatele (nebo dialektu), jak je uvedeno v definici schématu úložiště.

V opačném případě cíl představuje tabulku nebo zobrazení. Jeho předpona schématu je buď ve vlastnosti metadata schématu, pokud není null, jinak je název kontejneru entity.  Název tabulky nebo zobrazení je buď vlastnost "Table" (metadata), pokud není null, jinak vlastnost Name základu sady entit.

Všechny tyto vlastnosti pocházejí z definice odpovídajícího objektu EntitySet v souboru definice schématu úložiště (SSDL).

### <a name="using-primitive-types"></a>Používání primitivních typů

Při odkazování primitivních typů ve výstupních stromových příkazech jsou obvykle odkazovány v primitivních typech koncepčního modelu. Pro určité výrazy ale poskytovatelé potřebují odpovídající primitivní typ úložiště. Příklady takových výrazů zahrnují DbCastExpression a případně DbNullExpression, pokud poskytovatel potřebuje přetypovat hodnotu null na odpovídající typ. V těchto případech by poskytovatelé měli provést mapování na typ poskytovatele na základě primitivního typu a jeho omezujících vlastností.

## <a name="see-also"></a>Viz také:

- [Generování SQL](sql-generation.md)
