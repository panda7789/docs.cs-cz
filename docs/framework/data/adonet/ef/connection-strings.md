---
title: Připojovací řetězce v Entity Framework ADO.NET
description: Přečtěte si o připojovacích řetězcích v Entity Framework, které obsahují informace pro připojení k poskytovateli dat ADO.NET a o modelech a mapování souborů.
ms.date: 10/15/2018
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
ms.openlocfilehash: 2ae25f5881c033a84d65f5b0b4ed14b4866dbcb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286867"
---
# <a name="connection-strings-in-the-adonet-entity-framework"></a>Připojovací řetězce v Entity Framework ADO.NET

Připojovací řetězec obsahuje inicializační informace, které jsou předány jako parametr od poskytovatele dat ke zdroji dat. Syntaxe závisí na poskytovateli dat a připojovací řetězec se analyzuje během pokusu o otevření připojení. Připojovací řetězce, které používá Entity Framework, obsahují informace, které slouží k připojení k základnímu poskytovateli dat ADO.NET, který podporuje Entity Framework. Obsahují také informace o požadovaném modelu a mapování souborů.

Připojovací řetězec je používán poskytovatelem EntityClient při přístupu k modelu a mapování metadat a připojení ke zdroji dat. K připojovacímu řetězci lze přejít nebo nastavit <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> vlastnost <xref:System.Data.EntityClient.EntityConnection> . <xref:System.Data.EntityClient.EntityConnectionStringBuilder>Třída se dá použít k programovému vytváření nebo přístupu k parametrům v připojovacím řetězci. Další informace naleznete v tématu [How to: Build a EntityConnection Connection String](how-to-build-an-entityconnection-connection-string.md).

[Nástroje model EDM (Entity Data Model)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) generují připojovací řetězec, který je uložen v konfiguračním souboru aplikace. <xref:System.Data.Objects.ObjectContext>Tyto informace o připojení načítají automaticky při vytváření dotazů na objekty. <xref:System.Data.EntityClient.EntityConnection>Z vlastnosti, kterou používá instance, se <xref:System.Data.Objects.ObjectContext> dá dostat <xref:System.Data.Objects.ObjectContext.Connection%2A> . Další informace najdete v tématu [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100)).

## <a name="connection-string-syntax"></a>Syntaxe připojovacího řetězce

Další informace o obecné syntaxi připojovacích řetězců najdete v tématu [syntaxe připojovacího řetězce | Připojovací řetězce v ADO.NET](../connection-strings.md#connection-string-syntax).

## <a name="connection-string-parameters"></a>Parametry připojovacího řetězce

V následující tabulce jsou uvedeny platné názvy pro hodnoty klíčového slova v <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> .

|Klíčové slovo|Popis|
|-------------|-----------------|
|`Provider`|Povinné, pokud `Name` klíčové slovo není zadáno. Název zprostředkovatele, který se používá k načtení <xref:System.Data.Common.DbProviderFactory> objektu pro základního poskytovatele. Tato hodnota je konstantní.<br /><br /> Pokud `Name` klíčové slovo není zahrnuto v připojovacím řetězci entity, je vyžadována neprázdná hodnota pro `Provider` klíčové slovo. Toto klíčové slovo se vzájemně vylučuje pomocí `Name` klíčového slova.|
|`Provider Connection String`|Nepovinný parametr. Určuje připojovací řetězec specifický pro konkrétního zprostředkovatele, který se předává základnímu zdroji dat. Tento připojovací řetězec obsahuje platné páry klíč-hodnota pro poskytovatele dat. Neplatný způsobí `Provider Connection String` chybu za běhu, když je vyhodnocen zdrojem dat.<br /><br /> Toto klíčové slovo se vzájemně vylučuje pomocí `Name` klíčového slova.<br /><br /> Zajistěte, aby se hodnota vyhnula v souladu s obecnou syntaxí [připojovacích řetězců ADO.NET](../connection-strings.md). Zvažte například následující připojovací řetězec: `Server=serverName; User ID = userID` . Musí být uvozena řídicím znakem, protože obsahuje středník. Vzhledem k tomu, že neobsahuje dvojité uvozovky, mohou být použity pro uvozovací znaky:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`|
|`Metadata`|Povinné, pokud `Name` klíčové slovo není zadáno. Seznam adresářů, souborů a umístění prostředků oddělených kanálem, v nichž budou hledány metadata a informace o mapování. Například:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Prázdné mezery na každé straně oddělovače kanálu jsou ignorovány.<br /><br /> Toto klíčové slovo se vzájemně vylučuje pomocí `Name` klíčového slova.|
|`Name`|Aplikace může volitelně zadat název připojení v konfiguračním souboru aplikace, který poskytuje požadované hodnoty připojovacího řetězce klíč/hodnota. V takovém případě je nemůžete přímo do připojovacího řetězce zadávat. `Name`Klíčové slovo není v konfiguračním souboru povoleno.<br /><br /> Pokud `Name` klíčové slovo není zahrnuto v připojovacím řetězci, je požadováno neprázdné hodnoty pro klíčové slovo Provider.<br /><br /> Toto klíčové slovo se vzájemně vylučuje se všemi ostatními klíčovými slovy připojovacího řetězce.|

Následuje příklad připojovacího řetězce pro [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) uložený v konfiguračním souboru aplikace:

## <a name="model-and-mapping-file-locations"></a>Umístění souborů modelů a mapování

`Metadata`Parametr obsahuje seznam umístění pro `EntityClient` poskytovatele vyhledávání modelů a mapování souborů. Soubory modelů a mapování jsou často nasazeny ve stejném adresáři jako spustitelný soubor aplikace. Tyto soubory lze také nasadit do konkrétního umístění nebo zahrnout jako vložený prostředek do aplikace.

Vložené prostředky jsou zadány takto:

`Metadata=res://<assemblyFullName>/<resourceName>`

Pro definování umístění vloženého prostředku jsou k dispozici následující možnosti:

|Možnost|Popis|
|-|-|
|`assemblyFullName`|Úplný název sestavení s vloženým prostředkem. Název obsahuje jednoduchý název, název verze, podporovanou jazykovou verzi a veřejný klíč, a to následujícím způsobem:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Prostředky je možné vložit do libovolného sestavení, které je přístupné pro aplikaci.<br /><br /> Pokud zadáte zástupný znak ( \* ) pro `assemblyFullName` , Entity Framework runtime vyhledá prostředky v následujících umístěních, v tomto pořadí:<br /><br /> 1. volající sestavení.<br />2. odkazovaná sestavení.<br />3. sestavení v adresáři bin aplikace.<br /><br /> Pokud soubory nejsou v jednom z těchto umístění, bude vyvolána výjimka. **Poznámka:**  Použijete-li zástupný znak (*), Entity Framework musí vyhledat všechna sestavení pro prostředky se správným názvem. Chcete-li zvýšit výkon, zadejte název sestavení místo zástupného znaku.|
|`resourceName`|Název zahrnutého prostředku, například AdventureWorksModel. csdl. Služby metadat budou hledat pouze soubory nebo prostředky s jedním z následujících přípon: CSDL,. ssdl nebo. MSL. Pokud `resourceName` parametr není zadán, budou načteny všechny prostředky metadat. Prostředky by měly mít jedinečné názvy v rámci sestavení. Je-li v různých adresářích sestavení definováno více souborů se stejným názvem, `resourceName` musí obsahovat strukturu složky před názvem prostředku, například název_složky. FileName. csdl.<br /><br /> `resourceName`není vyžadováno, pokud zadáte zástupný znak (*) pro `assemblyFullName` .|

> [!NOTE]
> Chcete-li zvýšit výkon, zahrňte prostředky do volajícího sestavení s výjimkou newebových scénářů, kde není odkaz na základní mapování a soubory metadat v volajícím sestavení.

Následující příklad načte všechny soubory modelu a mapování v volajícím sestavení, odkazovaných sestaveních a dalších sestaveních v adresáři bin aplikace.

```csharp
Metadata=res://*/
```

Následující příklad načte soubor model. csdl ze sestavení AdventureWorks a načte model. ssdl a model. MSL soubory z výchozího adresáře běžící aplikace.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl
```

Následující příklad načte tři zadané prostředky z konkrétního sestavení.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl
```

Následující příklad načte všechny vložené prostředky s příponami. csdl,. MSL a. ssdl ze sestavení.

```csharp
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/
```

V následujícím příkladu jsou načteny všechny prostředky v relativní cestě k souboru a "datadir\metadata \\ " z načteného umístění sestavení.

```csharp
Metadata=datadir\metadata\
```

V následujícím příkladu jsou načteny všechny prostředky v relativní cestě k souboru z načteného umístění sestavení.

```csharp
Metadata=.\
```

## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Podpora pro &#124;DataDirectory&#124; náhradní řetězec a kořenový operátor webové aplikace (~)

`DataDirectory`a operátor ~ se používá v rámci <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> `Metadata` `Provider Connection String` klíčových slov a. <xref:System.Data.EntityClient.EntityConnection>Posune `DataDirectory` operátor a ~ do <xref:System.Data.Metadata.Edm.MetadataWorkspace> a poskytovatele úložiště, v uvedeném pořadí.

|Pojem|Popis|
|----------|-----------------|
|`&#124;DataDirectory&#124;`|Přeloží na relativní cestu k mapování a souborům metadat. Toto je hodnota, která je nastavena `AppDomain.SetData("DataDirectory", objValue)` metodou. `DataDirectory`Náhradní řetězec musí být ohraničen znaky kanálu a nesmí obsahovat žádné mezery mezi jeho názvem a znaky kanálu. V `DataDirectory` názvu se nerozlišují velká a malá písmena.<br /><br /> Pokud je třeba předat fyzický adresář s názvem "DataDirectory" jako člen seznamu cest metadat, přidejte prázdné znaky do buď nebo do obou stran názvu. Příklad: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Aplikace ASP.NET překládá &#124;&#124; DataDirectory do \<application root> složky/App_Data.|
|~|Přeloží se na kořenový adresář webové aplikace. Znak ~ na úvodní pozici je vždy interpretován jako kořenový operátor webové aplikace (~), i když může představovat platný místní podadresář. Chcete-li odkazovat na takový místní podadresář, měl by uživatel explicitně předat `./~` .|

`DataDirectory`a operátor ~ by měl být zadán pouze na začátku cesty, nebudou přeloženy na žádné jiné pozici. Entity Framework se pokusí řešení vyřešit `~/data` , ale bude považován `/data/~` za fyzickou cestu.

Cesta začínající `DataDirectory` operátorem nebo ~ nemůže překládat na fyzickou cestu mimo větev `DataDirectory` a operátoru ~. Například následující cesty budou přeloženy: `~` , `~/data` , `~/bin/Model/SqlServer` . Následující cesty se nedaří vyřešit: `~/..` , `~/../other` .

`DataDirectory`a operátor ~ lze rozšířit tak, aby zahrnoval podadresáře následujícím způsobem: `|DataDirectory|\Model` ,`~/bin/Model`

Rozlišení `DataDirectory` náhradního řetězce a operátor ~ nejsou rekurzivní. Například pokud `DataDirectory` obsahuje `~` znak, dojde k výjimce. Tím zabráníte nekonečné rekurzi.

## <a name="see-also"></a>Viz také

- [Práce se zprostředkovateli dat](working-with-data-providers.md)
- [Požadavky na nasazení](deployment-considerations.md)
- [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [Připojovací řetězce](../connection-strings.md)
