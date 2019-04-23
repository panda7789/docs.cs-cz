---
title: Schéma databáze trvalosti
ms.date: 03/30/2017
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
ms.openlocfilehash: 38df4b3d629840f1b5def2eafa0d074a2b2397a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767991"
---
# <a name="persistence-database-schema"></a>Schéma databáze trvalosti
Toto téma popisuje, veřejné zobrazení podporována Store Instance pracovního postupu SQL.  
  
## <a name="instances-view"></a>Zobrazení instancí  
 **Instance** zobrazení obsahuje obecné informace o všech instancí pracovních postupů v databázi.  
  
|Název sloupce|Typ sloupce|Popis|  
|-----------------|-----------------|-----------------|  
|InstanceId|UniqueIdentifier|ID instance pracovního postupu.|  
|PendingTimer|DateTime|Označuje, že pracovní postup je blokována v aktivitě Delay a bude pokračovat po vypršení platnosti časovač. Tato hodnota může být null, pokud pracovní postup není blokován čekání na časovač vypršení platnosti.|  
|CreationTime|DateTime|Určuje, kdy byla vytvořena pracovní postup.|  
|LastUpdatedTime|DateTime|Označuje čas posledního pracovního postupu byla trvale uložena do databáze.|  
|ServiceDeploymentId|BigInt|Funguje jako cizí klíč k zobrazení [ServiceDeployments]. Pokud se aktuální instance pracovního postupu je instance hostované webové služby, tento sloupec obsahuje hodnotu, jinak je nastavena na hodnotu NULL.|  
|SuspensionExceptionName|Nvarchar(450)|Určuje typ výjimky (například InvalidOperationException), která způsobila pracovní postup pro dočasné pozastavení.|  
|SuspensionReason|Nvarchar(max)|Označuje, proč byl pozastaven Instance pracovního postupu. Je-li k výjimce instance, kterou chcete pozastavit, tento sloupec obsahuje zprávy související s výjimkou.<br /><br /> Pokud instance byla ručně pozastavena, tento sloupec obsahuje uživatelem zadané důvod pro pozastavení instance.|  
|ActiveBookmarks|Nvarchar(max)|Pokud Instance pracovního postupu je nečinný, tato vlastnost určuje, jaké záložky instance je blokována v. Pokud Instance není nečinný, je tento sloupec NULL.|  
|CurrentMachine|Nvarchar(128)|Označuje, že název počítače má aktuálně pracovního postupu, které Instance načtena do paměti.|  
|LastMachine|Nvarchar(450)|Označuje poslední počítači, který je načíst instanci pracovního postupu.|  
|ExecutionStatus|Nvarchar(450)|Označuje aktuální stav provádění pracovního postupu. Možné stavy zahrnout **zpracování**, **nečinný**, **uzavřeno**.|  
|IsInitialized|Bit|Určuje, zda instance pracovního postupu byla inicializována. Instance pracovního postupu inicializované je instance pracovního postupu, který obsahuje alespoň jednou trvalé.|  
|IsSuspended|Bit|Určuje, zda instance pracovního postupu bylo pozastaveno.|  
|IsCompleted|Bit|Určuje, zda Instance pracovního postupu byl dokončen. **Poznámka:**  IIf **InstanceCompletionAction** je nastavena na **DeleteAll**, instance se odeberou ze zobrazení po dokončení.|  
|EncodingOption|TinyInt|Popisuje kódování použité k serializaci dat vlastnosti.<br /><br /> -0 – bez kódování<br />-   1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary(max)|Obsahuje vlastnosti serializovanou instanci dat, které vám poskytneme zpět do modulu Runtime pracovního postupu při načtení instance.<br /><br /> Každý primitivní vlastnost je nativní typ CLR, což znamená, že k deserializaci objektu blob nejsou potřeba žádné speciální sestavení.|  
|WriteOnlyPrimitiveDataProperties|Varbinary(max)|Obsahuje vlastnosti dat serializovanou instanci, které nejsou k dispozici zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Každý primitivní vlastnost je nativní typ CLR, což znamená, že k deserializaci objektu blob nejsou potřeba žádné speciální sestavení.|  
|ReadWriteComplexDataProperties|Varbinary(max)|Obsahuje vlastnosti serializovanou instanci dat, které vám poskytneme zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Deserializátor by vyžadují znalost typů objektů uložených v tento objekt blob.|  
|WriteOnlyComplexDataProperties|Varbinary(max)|Obsahuje vlastnosti dat serializovanou instanci, které nejsou k dispozici zpět do modulu runtime pracovního postupu při načtení instance.<br /><br /> Deserializátor by vyžadují znalost typů objektů uložených v tento objekt blob.|  
|IdentityName|Nvarchar(max)|Název definice pracovního postupu.|  
|IdentityPackage|Nvarchar(max)|Informace o balíčku zadaný při vytvoření pracovního postupu (jako je název sestavení).|  
|Sestavení|BigInt|Číslo sestavení verze pracovního postupu.|  
|Hlavní|BigInt|Hlavní číslo verze pracovního postupu.|  
|Vedlejší|BigInt|Vedlejší číslo verze pracovního postupu.|  
|Revize|BigInt|Číslo revize verze pracovního postupu.|  
  
> [!CAUTION]
>  **Instance** zobrazení také obsahuje aktivační události odstranění. Uživatelé s příslušnými oprávněními může provádět příkazy delete pro toto zobrazení, které odeberete vynuceně instancí pracovních postupů z databáze. Doporučujeme odstranit přímo ze zobrazení pouze jako poslední možnost, protože odstranění instance z pod modulu runtime pracovního postupu by mohlo způsobit nežádoucí důsledky. Místo toho použijte koncový bod správy Instance pracovního postupu modulu runtime pracovního postupu ukončení instance. Pokud chcete odstranit ze zobrazení pro velký počet instancí, ujistěte se, že nejsou žádné aktivní moduly runtime, který by mohl pracovat v těchto instancích.  
  
## <a name="servicedeployments-view"></a>ServiceDeployments zobrazení  
 **ServiceDeployments** zobrazení obsahuje informace o nasazení pro celý Web (služba IIS / WAS) hostovaných služeb pracovního postupu. Každá instance workflowu, který je hostitelem webové bude obsahovat **ServiceDeploymentId** , který odkazuje na řádek v tomto zobrazení.  
  
|Název sloupce|Typ sloupce|Popis|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|Primární klíč pro toto zobrazení.|  
|SiteName|Nvarchar(max)|Představuje název webu, který obsahuje služba pracovního postupu (třeba **výchozí webový server**).|  
|RelativeServicePath|Nvarchar(max)|Představuje virtuální cestu relativní vzhledem k lokalitě, která odkazuje na službu pracovního postupu. (např.)  **/app1/PurchaseOrderService.svc**).|  
|RelativeApplicationPath|Nvarchar(max)|Představuje virtuální cestu relativní vzhledem k lokalitě, která odkazuje na aplikaci, která obsahuje službu pracovního postupu. (například **/app1**).|  
|ServiceName|Nvarchar(max)|Představuje název pracovního postupu služby. (například **PurchaseOrderService**).|  
|ServiceNamespace|Nvarchar(max)|Představuje obor názvů služby pracovního postupu. (například **společnost**).|  
  
 Zobrazení ServiceDeployments také obsahuje aktivační události odstranění. Uživatelé s příslušnými oprávněními může provádět příkazy delete pro toto zobrazení můžete odebrat ServiceDeployment položky z databáze. Všimněte si, že:  
  
1. Odstranění položek z tohoto zobrazení je nákladná, jelikož celé databáze musí být uzamčen před provedením této operace. To je nezbytné Vyhýbejte se situacím, kdy Instance pracovního postupu může odkazovat na neexistující záznam ServiceDeployment. Odstranit z tohoto zobrazení pouze během dolů časy a časová období údržby.  
  
2. Žádný pokus o odstranění řádku ServiceDeployment, které se odkazuje položky v **instance** zobrazení bude mít za následek no-op. Můžete ho jenom odstranit řádky ServiceDeployment s nulovou odkazy.  
  
## <a name="instancepromotedproperties-view"></a>InstancePromotedProperties zobrazení  
 **InstancePromotedProperties** zobrazení obsahuje informace o propagované vlastnosti, které jsou zadány uživatelem. Propagovanou vlastnost funguje jako vlastnost první třídy, které může uživatel používat v dotazech načtení instancí.  Uživatel může například přidat PurchaseOrder propagační akce, která vždy ukládá náklady na pořadí, v **hodnota1** sloupce. To by umožnilo uživatele k dotazu na všechny nákupních objednávek, jejichž náklady překročí určitou hodnotu.  
  
|Typ sloupce|Typ sloupce|Popis|  
|-|-|-|  
|InstanceId|UniqueIdentifier|ID Instance pracovního postupu|  
|EncodingOption|TinyInt|Popisuje kódování použité k serializaci přesunutá binárních vlastností.<br /><br /> -0 – bez kódování<br />-   1 – GZipStream|  
|PromotionName|Nvarchar(400)|Název přidružený k této instanci podporu. PromotionName je potřeba k přidání kontextu do obecného sloupce v tomto řádku.<br /><br /> Například PromotionName PurchaseOrder může znamenat, že hodnota1 obsahuje náklady na pořadí, hodnota2 obsahuje jméno zákazníka, který objednávku vystavil, obsahuje hodnotu 3 adresu zákazníka a tak dále.|  
|Hodnota [1-32]|SqlVariant|Hodnota [1-32] obsahuje hodnoty, které mohou být uloženy ve sloupci hodnotu SqlVariant. V rámci jednoho propagační akce nemůže obsahovat více než 32 SqlVariants.|  
|Hodnota [33-64]|Varbinary(max)|Hodnota [33-64] obsahuje serializované hodnoty. Například Value33 by mohla obsahovat JPEG položky nakupuje. V rámci jednoho propagační akce nemůže obsahovat více než 32 binárních vlastností|  
  
 Zobrazení InstancePromotedProperties je vázán, což znamená, že uživatelé můžou přidávat indexy na jeden nebo více sloupců k optimalizaci dotazů na toto zobrazení schématu.  
  
> [!NOTE]
>  Indexované zobrazení vyžaduje další úložiště a přidá další nároky na zpracování. Najdete [zlepšení výkonu pomocí SQL Server 2008 indexovaných zobrazení](https://go.microsoft.com/fwlink/?LinkId=179529) Další informace.
