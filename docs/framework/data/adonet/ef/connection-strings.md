---
title: "Připojovací řetězce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d516bc-c99f-4865-8ff1-d856bc1a01c0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 64f2d0fbc54900443046bd2c71215cc0928c8658
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="connection-strings"></a>Připojovací řetězce
Připojovací řetězec obsahuje inicializace informace, které se předá jako parametr ze zprostředkovatele dat pro zdroj dat. Syntaxe závisí na poskytovateli dat a připojovací řetězec je analyzovat při pokusu o otevření připojení. Připojovací řetězce, které používá rozhraní Entity Framework obsahují informace používané pro připojení k základní zprostředkovatel dat ADO.NET, který podporuje rozhraní Entity Framework. Také obsahují informace o požadované modelu a mapování souborů.  
  
 Připojovací řetězec se používá zprostředkovatel EntityClient při přístupu k modelu a mapování metadat a připojení ke zdroji dat. Připojovací řetězec lze získat přístup nebo nastavit prostřednictvím <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> vlastnost <xref:System.Data.EntityClient.EntityConnection>. <xref:System.Data.EntityClient.EntityConnectionStringBuilder> Třídu lze použít prostřednictvím kódu programu vytvořit nebo získat přístup k parametry v připojovacím řetězci. Další informace najdete v tématu [postupy: sestavení řetězec připojení EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
 [Entity Data Model tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527) generovat připojovací řetězec, který je uložený v konfiguračním souboru aplikace. <xref:System.Data.Objects.ObjectContext>načte informace o tomto připojení automaticky při vytváření objektu dotazy. <xref:System.Data.EntityClient.EntityConnection> Používané <xref:System.Data.Objects.ObjectContext> instance je přístupná z <xref:System.Data.Objects.ObjectContext.Connection%2A> vlastnost. Další informace najdete v tématu [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99).  
  
## <a name="connection-string-parameters"></a>Parametry řetězce připojení  
 Formát připojovací řetězec je oddělený středníkem seznam párů klíč/hodnota parametru:  
  
 `keyword1=value; keyword2=value;`  
  
 Rovná se (=) připojí each – klíčové slovo a jeho hodnotu. Klíčová slova nejsou velká a malá písmena a mezery mezi páry klíč/hodnota jsou ignorovány. Hodnoty mohou být velká a malá písmena, v závislosti na zdroji dat. Všechny hodnoty, které obsahují středníkem, apostrofech nebo dvojité uvozovky musí být uzavřena v uvozovkách. Následující tabulka uvádí platné názvy hodnoty – klíčové slovo v <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A>.  
  
|– Klíčové slovo|Popis|  
|-------------|-----------------|  
|`Provider`|Požadováno pokud `Name` – klíčové slovo není zadán. Název zprostředkovatele, který se používá k načtení <xref:System.Data.Common.DbProviderFactory> objekt pro výchozí zprostředkovatel. Tato hodnota je konstantní.<br /><br /> Když `Name` – klíčové slovo není zahrnut do připojovacího řetězce entity, neprázdnou hodnotu pro `Provider` je požadováno klíčové slovo. This – klíčové slovo je vzájemně se vylučuje s `Name` – klíčové slovo.|  
|`Provider Connection String`|Volitelné. Určuje specifický pro zprostředkovatele připojovací řetězec, který je předán na podkladový zdroj dat. Tento připojovací řetězec je vyjádřit pomocí dvojice platný – klíčové slovo/hodnota pro poskytovatele dat. Neplatný `Provider Connection String` způsobí, že chyba spuštění vyhodnocena datovým zdrojem.<br /><br /> This – klíčové slovo je vzájemně se vylučuje s `Name` – klíčové slovo.<br /><br /> Hodnota `Provider Connection String` musí být uzavřeny do uvozovek. Následuje příklad:<br /><br /> `Provider Connection String ="Server=serverName; User ID = userID";`<br /><br /> V následujícím příkladu není chystáte fungovat:<br /><br /> `Provider Connection String =Server=serverName; User ID = userID`|  
|`Metadata`|Požadováno pokud `Name` – klíčové slovo není zadán. Seznam s položkami oddělenými kanálu adresářů, soubory a umístění prostředků, ve kterém můžete vyhledat informace mapování a metadat. Následuje příklad:<br /><br /> `Metadata=`<br /><br /> `c:\model &#124; c:\model\sql\mapping.msl;`<br /><br /> Mezery na každé straně oddělovače kanálu se ignorují.<br /><br /> This – klíčové slovo je vzájemně se vylučuje s `Name` – klíčové slovo.|  
|`Name`|Aplikace můžete volitelně zadat název připojení v konfiguračním souboru aplikace, který obsahuje hodnoty požadované klíčového slova a hodnoty připojovacího řetězce. V takovém případě je nelze zadat přímo v připojovacím řetězci. `Name` Klíčové slovo není povoleno v konfiguračním souboru.<br /><br /> Když `Name` – klíčové slovo není zahrnutý v připojovacím řetězci, neprázdný hodnoty pro je požadováno klíčové slovo zprostředkovatele.<br /><br /> This – klíčové slovo je vzájemně se vylučuje s všechny ostatní připojovací řetězec klíčová slova.|  
  
 Tady je příklad připojovacího řetězce pro [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) uložené v konfiguračním souboru aplikace:  
  
  
  
## <a name="model-and-mapping-file-locations"></a>Model a mapování umístění souborů  
 `Metadata` Parametr obsahuje seznam umístění `EntityClient` zprostředkovatele pro vyhledání soubory mapování a modelu. Soubory mapování a modelu často nasazených ve stejném adresáři jako spustitelný soubor. Tyto soubory můžete také nasadit v konkrétní umístění nebo zahrnuty jako vložený prostředek v aplikaci.  
  
 Vložené prostředky jsou zadány následujícím způsobem:  
  
```  
Metadata=res://<assemblyFullName>/<resourceName>.   
```  
  
 Pro definování umístění vložený prostředek k dispozici jsou následující možnosti:  
  
|Možnost|Popis|  
|-|-|  
|`assemblyFullName`|Úplný název sestavení s vložený prostředek. Název obsahuje jednoduchý název, název verze, jazykové verze a veřejný klíč, následujícím způsobem:<br /><br /> `ResourceLib, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`<br /><br /> Prostředky lze vložit do libovolného sestavení, která je přístupná aplikací.<br /><br /> Pokud zadáte zástupný znak (\*) pro `assemblyFullName`, modul runtime rozhraní Entity Framework bude hledat prostředky v následujících umístěních, v tomto pořadí:<br /><br /> 1.  Volajícího sestavení.<br />2.  Odkazovaná sestavení.<br />3.  Sestavení v adresáři bin aplikace.<br /><br /> Pokud nejsou soubory v jednom z těchto umístění, bude vyvolána výjimka. **Poznámka:** při použití zástupný znak (*), rozhraní Entity Framework musí projděte všechny sestavení pro prostředky se správným názvem. Pokud chcete zvýšit výkon, zadejte název sestavení místo zástupný znak.|  
|`resourceName`|Název zahrnuté prostředků, jako je například AdvendtureWorksModel.csdl. Metadata služby bude pouze hledat soubory nebo prostředkům s jedním z následujících přípon: .csdl, .ssdl nebo .msl. Pokud `resourceName` není zadán, bude možné načíst všechny prostředky metadat. Prostředky by měly mít jedinečné názvy v rámci sestavení. Je-li definována více souborů se stejným názvem do různých adresářů v sestavení, `resourceName` musí zahrnovat struktura složek před název prostředku, například FolderName.FileName.csdl.<br /><br /> `resourceName`není vyžadován při zadávání zástupný znak (*) pro `assemblyFullName`.|  
  
> [!NOTE]
>  Pokud chcete zvýšit výkon, prostředky pro vložení v volajícího sestavení, s výjimkou ve scénářích jiných webových kde neexistuje žádný odkaz na základní soubory mapování a metadat v volajícího sestavení.  
  
 Následující příklad načte všechny modelu a mapování souborů v volajícího sestavení, odkazovaná sestavení a ostatních sestavení v adresáři bin aplikace.  
  
```  
Metadata=res://*/  
```  
  
 Následující příklad načte soubor model.csdl ze sestavení AdventureWorks a načte model.ssdl a model.msl soubory z adresáře výchozí běžící aplikaci.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|model.ssdl|model.msl  
```  
  
 Následující příklad načte tři zadané prostředky z konkrétní sestavení.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.csdl|   
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.ssdl|   
res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/model.msl  
```  
  
 Následující příklad načte všechny vložené prostředky s rozšíření .csdl, .ssdl a .msl ze sestavení.  
  
```  
Metadata=res://AdventureWorks, 1.0.0.0, neutral, a14f3033def15840/  
```  
  
 Následující příklad načte všechny prostředky v relativní cesta k souboru plus "datadir\metadata\\" z umístění načíst sestavení.  
  
```  
Metadata=datadir\metadata\  
```  
  
 Následující příklad načte všechny prostředky v relativní cesta k souboru z umístění načíst sestavení.  
  
```  
Metadata=.\  
```  
  
## <a name="support-for-the-124datadirectory124-substitution-string-and-the-web-application-root-operator-"></a>Podpora pro &#124; DataDirectory &#124; Náhradní řetězec a kořenové operátor webových aplikací (~)  
 `DataDirectory`a ~ operátor používají <xref:System.Data.EntityClient.EntityConnection.ConnectionString%2A> jako součást `Metadata` a `Provider Connection String` klíčová slova. <xref:System.Data.EntityClient.EntityConnection> Předává `DataDirectory` a ~ operátor a <xref:System.Data.Metadata.Edm.MetadataWorkspace> a zprostředkovatele úložiště v uvedeném pořadí.  
  
|Termín|Popis|  
|----------|-----------------|  
|`&#124;DataDirectory&#124;`|Přeloží na relativní cestu k souborům mapování a metadat. Toto je hodnota, lze ji nastavit pomocí `AppDomain.SetData("DataDirectory", objValue)` metoda. `DataDirectory` Náhradní řetězec musí být uzavřena do kanálu znaků a nesmí být žádné mezery mezi jeho jméno a znaky kanálu. `DataDirectory` Název není malá a velká písmena.<br /><br /> Pokud fyzický adresář s názvem "DataDirectory" má být předán jako člen skupiny seznamu cest metadata, přidejte měli prázdné znaky na straně nebo obou stranách název, například: `Metadata="DataDirectory1 &#124; DataDirectory &#124; DataDirectory2"`. Aplikace technologie ASP.NET vyřeší &#124; DataDirectory &#124; na "\<kořenový adresář aplikace > / app_data" složky.|  
|~|Přeloží ke kořenové složce webové aplikace. ~ Znak, od počáteční pozice vždy interpretována jako operátor kořenové webových aplikací (~), i když ho může představovat platný podadresáři místní. K odkazování na místní podadresáři, musí uživatel explicitně předat `./~`.|  
  
 `DataDirectory`a ~ operátor musí být zadán pouze na začátku cestu, nejsou přeložit na jiné pozici. Rozhraní Entity Framework se pokusí přeložit `~/data`, ale bude považovat `/data/~` jako fyzická cesta.  
  
 Cestu, která začíná `DataDirectory` nebo ~ operátor nelze přeložit na fyzickou cestu mimo větev `DataDirectory` a ~ operátor. Například vyřešit následující cesty: `~` , `~/data` , `~/bin/Model/SqlServer`. Následující cesty se nepodaří vyřešit: `~/..`, `~/../other`.  
  
 `DataDirectory`a ~ operátor lze rozšířit zahrnout podadresářích, následujícím způsobem: `|DataDirectory|\Model`,`~/bin/Model`  
  
 Řešení `DataDirectory` náhradní řetězec a ~ operátor je tohoto nerekurzivního. Například když `DataDirectory` zahrnuje `~` znak, dojde k výjimce. Tím se zabrání nekonečná rekurze.  
  
## <a name="see-also"></a>Viz také  
 [Práce se zprostředkovateli dat](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)  
 [Důležité informace o nasazení](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [Připojovací řetězce](../../../../../docs/framework/data/adonet/connection-strings.md)
