---
title: 'Definování typů a jejich členů – prohlídka jazyka C #'
description: Stavební bloky programů jsou typy. Naučte se vytvářet třídy, struktury, rozhraní a další funkce v jazyce C#.
ms.date: 08/06/2020
ms.openlocfilehash: 69d6f0fe1e11f287fb5e385761fc210a61929d10
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88068525"
---
# <a name="types-and-members"></a>Typy a členové

## <a name="classes-and-objects"></a>Třídy a objekty

*Třídy* jsou základem typů jazyka C#. Třída je datová struktura, která kombinuje stav (pole) a akce (metody a další členy funkce) v jedné jednotce. Třída poskytuje definici pro *instance* třídy, označované také jako *objekty*. Třídy podporují *Dědičnost* a *polymorfismus*, mechanismy, kterými mohou *odvozené třídy* roztáhnout a specializovat *základní třídy*.

Nové třídy jsou vytvářeny pomocí deklarací třídy. Deklarace třídy začíná hlavičkou. Záhlaví určuje:

- Atributy a modifikátory třídy
- Název třídy
- Základní třída (při dědění ze [základní třídy](#base-classes))
- Rozhraní implementovaná třídou.

Pod hlavičkou následuje tělo třídy, které se skládá ze seznamu deklarací členů napsaných mezi oddělovači `{` a `}` .

Následující kód ukazuje deklaraci jednoduché třídy s názvem `Point` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

Instance tříd jsou vytvořeny pomocí `new` operátoru, který přiděluje paměť pro novou instanci, vyvolá konstruktor pro inicializaci instance a vrátí odkaz na instanci. Následující příkazy vytvoří dva `Point` objekty a ukládají odkazy na tyto objekty ve dvou proměnných:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

Paměť obsazená objektem je automaticky uvolněna v případě, že objekt již není dostupný. Není ani možné explicitně uvolnit objekty v jazyce C#.

### <a name="type-parameters"></a>Parametry typu

Obecné třídy definují [***parametry typu***](../programming-guide/generics/index.md). Parametry typu jsou seznam názvů parametrů typu uzavřených do lomených závorek. Parametry typu následují za názvem třídy. Parametry typu lze potom použít v těle deklarací třídy k definování členů třídy. V následujícím příkladu parametry typu `Pair` jsou `TFirst` a `TSecond` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

Typ třídy, která je deklarována pro přijetí parametrů typu, se nazývá *typ obecné třídy*. Typy struktury, rozhraní a delegátů můžou být také obecné.
Při použití obecné třídy je nutné zadat argumenty typu pro každý z parametrů typu:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

Obecný typ s poskytnutými argumenty typu, jako `Pair<int,string>` je například výše, se označuje jako *konstruovaný typ*.

### <a name="base-classes"></a>Základní třídy

Deklarace třídy může určovat základní třídu. Použijte název třídy a parametry typu s dvojtečkou a názvem základní třídy. Vynechání specifikace základní třídy je stejné jako odvození z typu `object` . V následujícím příkladu je základní třída třídy `Point3D` `Point` . V prvním příkladu je základní třída `Point` `object` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

Třída dědí členy své základní třídy. Dědičnost znamená, že třída implicitně obsahuje skoro všechny členy své základní třídy. Třída nedědí instance a statické konstruktory a finalizační metodu. Odvozená třída může přidat nové členy do těch členů, které dědí, ale nemůže odebrat definici zděděného člena. V předchozím příkladu `Point3D` dědí `X` `Y` Členové a z `Point` a každá `Point3D` instance obsahuje tři vlastnosti, `X` , `Y` a `Z` .

Implicitní převod existuje z typu třídy na libovolný z jeho základních typů třídy. Proměnná typu třídy může odkazovat na instanci této třídy nebo instance jakékoli odvozené třídy. Například s ohledem na předchozí deklarace třídy může proměnná typu `Point` odkazovat buď na, `Point` nebo `Point3D` :

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a>Struktury

Třídy definují typy, které podporují dědičnost a polymorfismuy. Umožňují vytvářet sofistikovaná chování založená na hierarchiích odvozených tříd. Naopak typy [***struktury***](../language-reference/builtin-types/struct.md) jsou jednodušší typy, jejichž primárním účelem je ukládání hodnot dat. Struktury nemůžou deklarovat základní typ; implicitně se odvozují z <xref:System.ValueType?displayProperty=nameWithType> . Z typu nelze odvodit jiné `struct` typy `struct` . Jsou implicitně zapečetěné.

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a>Rozhraní

[***Rozhraní***](../programming-guide/interfaces/index.md) definuje kontrakt, který může být implementován pomocí tříd a struktur. Rozhraní může obsahovat metody, vlastnosti, události a indexery. Rozhraní obvykle neposkytuje implementace členů, které definuje – určuje pouze členy, které musí být poskytnuty třídami nebo strukturami, které implementují rozhraní.

Rozhraní mohou využívat ***vícenásobnou dědičnost***. V následujícím příkladu rozhraní `IComboBox` dědí z `ITextBox` a `IListBox` .

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

Třídy a struktury mohou implementovat více rozhraní. V následujícím příkladu třída `EditBox` implementuje i `IControl` `IDataBound` .

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

Pokud třída nebo struktura implementuje konkrétní rozhraní, instance této třídy nebo struktury lze implicitně převést na tento typ rozhraní. Například

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a>Výčty

Typ [***výčtu***](../language-reference/builtin-types/enum.md) definuje sadu konstantních hodnot. Následující `enum` deklaruje konstanty, které definují jinou kořenovou zeleninu:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

Můžete také definovat `enum` , který má být použit v kombinaci jako příznaky. Následující deklarace deklaruje sadu příznaků pro čtyři období. Může se použít libovolná kombinace období, včetně `All` hodnoty, která zahrnuje všechny sezóny:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

Následující příklad ukazuje deklarace obou předchozích výčtů:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a>Typy nullable

Proměnné libovolného typu mohou být deklarovány jako ***nenulové nebo*** ***null***. Proměnná s možnou hodnotou null může obsahovat další `null` hodnotu, což značí, že žádná hodnota neexistuje. Typy hodnot s možnou hodnotou null (struktury nebo výčty) jsou reprezentovány <xref:System.Nullable%601?displayProperty=nameWithType> . Typy odkazů, které nejsou null a povolující hodnotu null, jsou reprezentované podkladovým typem odkazu. Rozlišení je reprezentované metadaty, které načte kompilátor a některé knihovny. Kompilátor poskytuje upozornění, když jsou odkazy na hodnotu null překážené bez prvotní kontroly jejich hodnoty `null` . Kompilátor také poskytuje upozornění, pokud jsou odkazy, které nejsou null, přiřazeny k hodnotě, která může být `null` . Následující příklad deklaruje ***hodnotu null int***a inicializuje ji na `null` . Potom nastaví hodnotu na `5` . Ukazuje stejný koncept s ***připouštějící řetězec s možnou hodnotou null***. Další informace naleznete v tématu [typy hodnot](../language-reference/builtin-types/nullable-value-types.md) s možnou hodnotou null a [odkazy s možnou hodnotou null](../nullable-references.md).

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a>N-tice

Jazyk C# podporuje [***řazené kolekce členů***](../language-reference/builtin-types/value-tuples.md), které poskytují stručnou syntaxi pro seskupení více datových prvků ve zjednodušené datové struktuře. Vytvořte instanci řazené kolekce členů deklarováním typů a názvů členů mezi `(` a `)` , jak je znázorněno v následujícím příkladu:

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

Řazené kolekce členů poskytují alternativu pro strukturu dat s více členy, bez použití stavebních bloků popsaných v dalším článku.

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](program-building-blocks.md)
