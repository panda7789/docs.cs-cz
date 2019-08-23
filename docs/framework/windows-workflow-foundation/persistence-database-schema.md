---
title: Schéma databáze trvalosti
ms.date: 03/30/2017
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
ms.openlocfilehash: 384a9aceaf0b5619bbc4eca5929b6e6d7855e3d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962881"
---
# <a name="persistence-database-schema"></a>Schéma databáze trvalosti
Toto téma popisuje veřejné pohledy, které podporuje úložiště instance pracovního postupu SQL.  
  
## <a name="instances-view"></a>Zobrazení instancí  
 Zobrazení **Instances** obsahuje obecné informace o všech instancích pracovního postupu v databázi.  
  
|Název sloupce|Typ sloupce|Popis|  
|-----------------|-----------------|-----------------|  
|InstanceId|uniqueidentifier|ID instance pracovního postupu|  
|PendingTimer|DateTime|Indikuje, že je pracovní postup zablokovaný u aktivity zpoždění a bude obnoven po vypršení platnosti časovače. Tato hodnota může být null, pokud pracovní postup není blokovaný čekáním na vypršení platnosti časovače.|  
|CreationTime|DateTime|Určuje, kdy byl pracovní postup vytvořen.|  
|LastUpdatedTime|DateTime|Označuje čas, kdy byl pracovní postup naposledy trvale uložen do databáze.|  
|ServiceDeploymentId|BigInt|Slouží jako cizí klíč k zobrazení [ServiceDeployments]. Pokud je aktuální instance pracovního postupu instancí služby hostované na webu, pak má tento sloupec hodnotu, v opačném případě je nastavená na hodnotu NULL.|  
|SuspensionExceptionName|Nvarchar(450)|Určuje typ výjimky (např. InvalidOperationException), která způsobila pozastavení pracovního postupu.|  
|SuspensionReason|Nvarchar (max)|Indikuje, proč se instance pracovního postupu pozastavila. Pokud výjimka způsobila pozastavení instance, pak tento sloupec obsahuje zprávu spojenou s výjimkou.<br /><br /> Pokud byla instance ručně pozastavena, pak tento sloupec obsahuje důvod uživatele určený k pozastavení instance.|  
|ActiveBookmarks|Nvarchar (max)|Pokud je instance pracovního postupu nečinná, tato vlastnost indikuje, na kterých záložkách je instance zablokovaná. Pokud instance není nečinná, je tento sloupec NULL.|  
|CurrentMachine|Nvarchar (128)|Označuje, že název počítače v současné době má instanci pracovního postupu načtenou v paměti.|  
|LastMachine|Nvarchar(450)|Označuje poslední počítač, který načte instanci pracovního postupu.|  
|ExecutionStatus|Nvarchar(450)|Určuje aktuální stav provádění pracovního postupu. Mezi možné stavy patří **provádění**, nečinné, **Uzavřeno**.|  
|IsInitialized|bit|Označuje, zda instance pracovního postupu byla inicializována. Inicializovaná instance pracovního postupu je instance pracovního postupu, která byla alespoň jednou trvalá.|  
|Pozastaveno|bit|Označuje, zda byla instance pracovního postupu pozastavena.|  
|IsCompleted|bit|Označuje, zda byla instance pracovního postupu dokončena. **Poznámka:**  IIF vlastnost **InstanceCompletionAction** je nastavená na **DeleteAll**, instance se po dokončení odeberou ze zobrazení.|  
|EncodingOption|TinyInt|Popisuje kódování používané k serializaci vlastností dat.<br /><br /> -0 – bez kódování<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary (max)|Obsahuje vlastnosti dat serializované instance, které budou poskytnuty zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Každá primitivní vlastnost je nativní typ CLR, což znamená, že k deserializaci objektu BLOB nejsou potřeba žádná speciální sestavení.|  
|WriteOnlyPrimitiveDataProperties|Varbinary (max)|Obsahuje vlastnosti dat serializované instance, které se při načtení instance neposkytují zpět do modulu runtime pracovního postupu.<br /><br /> Každá primitivní vlastnost je nativní typ CLR, což znamená, že k deserializaci objektu BLOB nejsou potřeba žádná speciální sestavení.|  
|ReadWriteComplexDataProperties|Varbinary (max)|Obsahuje vlastnosti dat serializované instance, které budou poskytnuty zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Odserializátor by vyžadoval znalost všech typů objektů uložených v tomto objektu BLOB.|  
|WriteOnlyComplexDataProperties|Varbinary (max)|Obsahuje vlastnosti dat serializované instance, které se při načtení instance neposkytují zpět do modulu runtime pracovního postupu.<br /><br /> Odserializátor by vyžadoval znalost všech typů objektů uložených v tomto objektu BLOB.|  
|IdentityName|Nvarchar (max)|Název definice pracovního postupu|  
|IdentityPackage|Nvarchar (max)|Informace o balíčku, které byly zadány v době, kdy byl pracovní postup vytvořen (například název sestavení).|  
|Sestavení|BigInt|Číslo sestavení verze pracovního postupu|  
|Hlavní|BigInt|Hlavní číslo verze pracovního postupu.|  
|Vedlejší|BigInt|Vedlejší číslo verze pracovního postupu|  
|Revize|BigInt|Číslo revize verze pracovního postupu|  
  
> [!CAUTION]
>  Zobrazení **Instances** obsahuje také aktivační událost DELETE. Uživatelé s příslušnými oprávněními mohou provádět příkazy odstranit pro toto zobrazení, které bude nuceně odebrat instance pracovního postupu z databáze. Doporučujeme odstranit přímo ze zobrazení jako poslední, protože odstranění instance z pod modulem runtime pracovního postupu by mohlo vést k nezamýšleným důsledkům. Místo toho použijte koncový bod správy instancí pracovního postupu, aby modul runtime pracovního postupu ukončil instanci. Pokud chcete ze zobrazení odstranit velký počet instancí, ujistěte se, že neexistují žádné aktivní moduly runtime, které by mohly na těchto instancích pracovat.  
  
## <a name="servicedeployments-view"></a>Zobrazení ServiceDeployments  
 Zobrazení **ServiceDeployments** obsahuje informace o nasazení pro všechny webové služby (služba IIS/was) hostované služby pracovního postupu. Každá instance pracovního postupu, která je hostitelem webu, bude obsahovat **ServiceDeploymentId** , který odkazuje na řádek v tomto zobrazení.  
  
|Název sloupce|Typ sloupce|Popis|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Primární klíč pro toto zobrazení|  
|SiteName|Nvarchar (max)|Představuje název webu, který obsahuje službu pracovního postupu (například **výchozí web**).|  
|RelativeServicePath|Nvarchar (max)|Představuje virtuální cestu relativní k lokalitě, která odkazuje na službu pracovního postupu. například.  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|Nvarchar (max)|Představuje virtuální cestu relativní k lokalitě, která odkazuje na aplikaci, která obsahuje službu pracovního postupu. (např. **/app1**).|  
|ServiceName|Nvarchar (max)|Představuje název služby pracovního postupu. (např. **PurchaseOrderService**).|  
|ServiceNamespace|Nvarchar (max)|Představuje obor názvů služby pracovního postupu. (např. **spolecnost**).|  
  
 Zobrazení ServiceDeployments obsahuje také aktivační událost DELETE. Uživatelé s příslušnými oprávněními mohou spustit příkazy odstranit v tomto zobrazení a odebrat tak položky ServiceDeployment z databáze. Všimněte si, že:  
  
1. Odstranění položek z tohoto zobrazení je nákladné, protože před provedením této operace musí být uzamčena celá databáze. To je nezbytné, aby se zabránilo situaci, kdy by mohla instance pracovního postupu odkazovat na neexistující položku ServiceDeployment. Odstranit z tohoto zobrazení pouze během doby mimo špičku nebo okna údržby.  
  
2. Při každém pokusu o odstranění řádku ServiceDeployment, na který se odkazuje pomocí položek v zobrazení Instances, dojde k tomu, že nebudete mít za následek no-op. ServiceDeployment řádky můžete odstranit pouze s nulovými odkazy.  
  
## <a name="instancepromotedproperties-view"></a>Zobrazení InstancePromotedProperties  
 Zobrazení **InstancePromotedProperties** obsahuje informace pro všechny propagované vlastnosti, které jsou určeny uživatelem. Propagovaná vlastnost je funkce jako vlastnost první třídy, kterou může uživatel použít v dotazech k načtení instancí.  Uživatel například může přidat povýšení PurchaseOrder, která vždy uloží náklady Objednávky do sloupce **hodnota1** . To umožní uživateli dotazovat se na všechny nákupní objednávky, jejichž náklady přesahují určitou hodnotu.  
  
|Typ sloupce|Typ sloupce|Popis|  
|-|-|-|  
|InstanceId|uniqueidentifier|ID instance pracovního postupu|  
|EncodingOption|TinyInt|Popisuje kódování používané k serializaci propagovaných binárních vlastností.<br /><br /> -0 – bez kódování<br />-   1 – GZipStream|  
|Povýšení|Nvarchar(400)|Název propagačního povýšení přidruženého k této instanci. K přidání kontextu do obecných sloupců v tomto řádku je potřeba povýšení.<br /><br /> Například povýšení PurchaseOrder by mohlo znamenat, že hodnota1 obsahuje náklady na objednávku, hodnota2 obsahuje jméno zákazníka, který objednávku zadal, hodnota 3 obsahuje adresu zákazníka atd.|  
|Hodnota [1-32]|Hodnotu SqlVariant|Hodnota [1-32] obsahuje hodnoty, které mohou být uloženy ve sloupci hodnotu SqlVariant. Jedna propagační akce nemůže obsahovat více než 32 SqlVariants.|  
|Hodnota [33-64]|Varbinary (max)|Hodnota [33-64] obsahuje serializované hodnoty. Například Value33 může obsahovat JPEG položky, která se kupuje. Jedna propagační akce nemůže obsahovat více než 32 binárních vlastností.|  
  
 Zobrazení InstancePromotedProperties je vázáno na schéma, což znamená, že uživatelé mohou přidávat indexy na jeden nebo více sloupců, aby bylo možné optimalizovat dotazy proti tomuto zobrazení.  
  
> [!NOTE]
> Indexované zobrazení vyžaduje větší úložiště a zvyšuje režijní náklady na zpracování. Další informace najdete [v tématu zvýšení výkonu pomocí indexovaných zobrazení SQL Server 2008](https://go.microsoft.com/fwlink/?LinkId=179529) .
