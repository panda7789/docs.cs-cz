---
title: Trvalost schématu databáze
ms.date: 03/30/2017
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
ms.openlocfilehash: 4dd49d08e522c842d0f21f176b4d77ac0adb4b47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="persistence-database-schema"></a>Trvalost schématu databáze
Toto téma popisuje veřejné zobrazení podporuje ukládání Instance pracovního postupu SQL.  
  
## <a name="instances-view"></a>Zobrazení instancí  
 **Instance** obsahuje obecné informace o všech instancí pracovního postupu v databázi.  
  
|Název sloupce|Typ sloupce|Popis|  
|-----------------|-----------------|-----------------|  
|identifikátor instanceId|Typ UniqueIdentifier|ID instance pracovního postupu.|  
|PendingTimer|DateTime|Označuje, že je na aktivitu zpoždění zablokovaný pracovního postupu a bude pokračovat. po vypršení platnosti časovač. Tato hodnota může být null, pokud pracovní postup není blokován čekání na časovač vyprší.|  
|Čas vytvoření|DateTime|Určuje, kdy byl vytvořen pracovní postup.|  
|LastUpdatedTime|DateTime|Označuje poslední čas, pracovní postup byl trvalé do databáze.|  
|ServiceDeploymentId|BigInt|Funguje jako cizí klíč do zobrazení [ServiceDeployments]. Pokud se aktuální instance pracovního postupu je instance webové hostované služby, tento sloupec obsahuje hodnotu, jinak hodnota je nastavena na hodnotu NULL.|  
|SuspensionExceptionName|Nvarchar(450)|Označuje typ výjimky (např. InvalidOperationException), která způsobila, že pozastavení pracovního postupu.|  
|SuspensionReason|nvarchar(max)|Označuje, proč byl pozastaven k instanci pracovního postupu. Pokud k výjimce instance pozastavit, tento sloupec obsahuje zprávu přidruženou výjimku.<br /><br /> Pokud instance byla ručně pozastavena, tento sloupec obsahuje pozastavení instance důvod zadaného uživatelem.|  
|ActiveBookmarks|nvarchar(max)|Pokud Instance pracovního postupu je nečinná, tato vlastnost určuje, jaké záložky instance je na zablokovaný. Pokud Instance není nečinná, tento sloupec je NULL.|  
|CurrentMachine|Nvarchar(128)|Označuje, že název počítače v současnosti má pracovní postup, který Instance načten do paměti.|  
|LastMachine|Nvarchar(450)|Označuje poslední počítači, který je načíst instanci pracovního postupu.|  
|ExecutionStatus|Nvarchar(450)|Označuje aktuální stav spuštění pracovního postupu. Možné stavy zahrnout **zpracování**, **nečinnosti**, **uzavřeno**.|  
|IsInitialized.|Bit|Určuje, zda byla inicializována k instanci pracovního postupu. Instance pracovního postupu inicializovaného je instance pracovního postupu, který obsahuje alespoň jednou trvalé.|  
|IsSuspended|Bit|Určuje, zda bylo pozastaveno k instanci pracovního postupu.|  
|IsCompleted|Bit|Určuje, zda Instance pracovního postupu byl dokončen. **Poznámka:** Iif **InstanceCompletionAction** je nastavena na **DeleteAll**, instance jsou odebrány ze zobrazení po dokončení.|  
|EncodingOption|TinyInt|Popisuje, kódování použité k serializaci dat vlastnosti.<br /><br /> -0 – bez kódování<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary(max)|Obsahuje vlastnosti data serializovaná instance, které se mají poskytnout zpět do modulu Runtime pracovního postupu při načtení instance.<br /><br /> Každou primitivní vlastnost je nativní typ CLR, což znamená, že žádné speciální sestavení jsou potřeba k deserializaci objektu blob.|  
|WriteOnlyPrimitiveDataProperties|Varbinary(max)|Obsahuje vlastnosti data serializovaná instance, které nejsou k dispozici zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Každou primitivní vlastnost je nativní typ CLR, což znamená, že žádné speciální sestavení jsou potřeba k deserializaci objektu blob.|  
|ReadWriteComplexDataProperties|Varbinary(max)|Obsahuje vlastnosti data serializovaná instance, které se mají poskytnout zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Deserializátor by vyžadují znalosti systému všechny typy objektů, které jsou uložené v této objektů blob.|  
|WriteOnlyComplexDataProperties|Varbinary(max)|Obsahuje vlastnosti data serializovaná instance, které nejsou k dispozici zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Deserializátor by vyžadují znalosti systému všechny typy objektů, které jsou uložené v této objektů blob.|  
|IdentityName|nvarchar(max)|Název definice pracovního postupu.|  
|IdentityPackage|nvarchar(max)|Informace o balíčku věnovat, když pracovní postup byl vytvořen (například název sestavení).|  
|Sestavení|BigInt|Číslo sestavení verze pracovního postupu.|  
|Hlavní|BigInt|Hlavní číslo verze pracovního postupu.|  
|Vedlejší|BigInt|Menší počet verze pracovního postupu.|  
|Revize|BigInt|Číslo revize verze pracovního postupu.|  
  
> [!CAUTION]
>  **Instance** zobrazení také obsahuje aktivační události odstranění. Uživatelé s příslušnými oprávněními může spustit příkazy odstranit toto zobrazení, která instance pracovního postupu vynuceně odstraní z databáze. Doporučujeme odstranění přímo ze zobrazení pouze jako poslední možnost, protože odstranění instance z pod modulu runtime pracovního postupu může mít za následek nežádoucích důsledků. Místo toho použijte koncový bod správy Instance pracovního postupu tak, aby měl modulu runtime pracovního postupu ukončení instance. Pokud chcete odstranit ze zobrazení velký počet instancí, ujistěte se, že neexistují žádné aktivní moduly runtime, který může pracovat na těchto instancích.  
  
## <a name="servicedeployments-view"></a>ServiceDeployments zobrazení  
 **ServiceDeployments** zobrazení obsahuje informace o nasazení pro celý Web (služby IIS / byl) hostované služby pracovních postupů. Každá instance workflowu, který je hostovaný Web bude obsahovat **ServiceDeploymentId** který odkazuje na řádek v tomto zobrazení.  
  
|Název sloupce|Typ sloupce|Popis|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Primární klíč pro toto zobrazení.|  
|SiteName|nvarchar(max)|Představuje název lokality, která obsahuje službu pracovního postupu (například **Default Web Site**).|  
|RelativeServicePath|nvarchar(max)|Představuje virtuální cestu vzhledem k lokalitě, která odkazuje na službu pracovního postupu. (např.)  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|nvarchar(max)|Představuje virtuální cestu vzhledem k lokalitě, která odkazuje na aplikaci, která obsahuje službu pracovního postupu. (například **app1**).|  
|ServiceName|nvarchar(max)|Představuje název pracovního postupu služby. (například **PurchaseOrderService**).|  
|ServiceNamespace|nvarchar(max)|Představuje obor názvů služby pracovního postupu. (například **Moje_firma**).|  
  
 Zobrazení ServiceDeployments také obsahuje aktivační události odstranění. Uživatelé s příslušnými oprávněními může spustit příkazy odstranění tohoto zobrazení a odebrání položek ServiceDeployment z databáze. Všimněte si, že:  
  
1.  Odstranění položek z tohoto hlediska je nákladná, protože je nutné uzamknout celé databáze, před provedením této operace. To je nezbytné Vyhýbejte se situacím, kdy Instance pracovního postupu může odkazovat na neexistující ServiceDeployment záznam. Odstraňte z tohoto hlediska pouze během dobu mimo provoz nebo časová období údržby.  
  
2.  Jakýkoli pokus o odstranění řádku ServiceDeployment, který se odkazuje položek v **instance** zobrazení bude mít za následek žádná operace. Odstranit lze pouze řádky ServiceDeployment s nulové odkazy.  
  
## <a name="instancepromotedproperties-view"></a>InstancePromotedProperties zobrazení  
 **InstancePromotedProperties** obsahuje informace pro všechny propagovaných vlastnosti, které jsou určené uživatele. Propagovaných vlastnost funguje jako první třídy vlastnosti, která může uživatel používat v dotazech načtení instancí.  Uživatel může například přidat PurchaseOrder povýšení, která vždy ukládá náklady na pořadí, v **Value1** sloupce. To by umožnilo uživatelům dotaz na všech nákupních objednávek, jejichž náklady překročí určitou hodnotu.  
  
|Typ sloupce|Typ sloupce|Popis|  
|-|-|-|  
|identifikátor instanceId|Typ UniqueIdentifier|ID Instance pracovního postupu|  
|EncodingOption|TinyInt|Popisuje, kódování použité k serializaci propagovaných binární vlastnosti.<br /><br /> -0 – bez kódování<br />-1 – GZipStream|  
|PromotionName|Nvarchar(400)|Název povýšení přidruženého k této instanci. PromotionName je potřeba přidat kontext na obecné sloupce v tomto řádku.<br /><br /> Například PromotionName PurchaseOrder by to znamenat, že Value1 obsahuje náklady na pořadí, Value2 obsahuje název odběratele, který zadal pořadí, obsahuje hodnotu 3 adresu zákazníka a tak dále.|  
|Hodnota [1-32]|Parametr SqlVariant|Hodnota [1-32] obsahuje hodnoty, které mohou být uloženy ve sloupci parametr SqlVariant. U jedné povýšení nesmí obsahovat víc než 32 SqlVariants.|  
|Hodnota [33-64]|Varbinary(max)|Hodnota [33-64] obsahuje serializovaných hodnot. Například Value33 mohou obsahovat JPEG položky se zakoupili. U jedné povýšení nesmí obsahovat víc než 32 binárních vlastností|  
  
 Zobrazení InstancePromotedProperties je vázán, což znamená, že uživatelé mohou přidat indexy jeden nebo více sloupců k optimalizaci dotazy pro toto zobrazení schématu.  
  
> [!NOTE]
>  Indexované zobrazení vyžaduje další úložiště a přidá další nároky na zpracování. Naleznete [zlepšení výkonu s indexované zobrazení serveru SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=179529) Další informace.
