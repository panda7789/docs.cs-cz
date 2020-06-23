---
title: Nástroj ServiceModel Metadata Utility (Svcutil.exe)
description: Přečtěte si o nástroji pro metadata ServiceModel, který generuje kód modelu služby WFC z dokumentů metadat a dokumentů metadat z kódu modelu služby.
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 9f8e8e0239f8f8cd149bc6e8b1d7921124731087
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245944"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>Nástroj ServiceModel Metadata Utility (Svcutil.exe)

Nástroj pro vytváření metadat třídy ServiceModel slouží ke generování kódu modelu služby z dokumentů metadat a dokumentů metadat z kódu modelu služby.

## <a name="svcutilexe"></a>SvcUtil.exe

Nástroj pro dodávající metadata se dá najít v umístění instalace Windows SDK, konkrétně *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin*.

### <a name="functionalities"></a>Funkce

V následující tabulce najdete přehled různých funkcí poskytovaných tímto nástrojem a příslušné téma, které popisuje, jak se používá:

|Úkol|Téma|
|----------|-----------|
|Generuje kód ze spuštěných služeb nebo statických dokumentů metadat.|[Generování klienta WCF z metadat služby](./feature-details/generating-a-wcf-client-from-service-metadata.md)|
|Exportuje dokumenty metadat z zkompilovaného kódu.|[Postupy: Použití nástroje Svcutil.exe pro export metadat z kompilovaného kódu služby](./feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|Ověří zkompilovaný kód služby.|[Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe](./feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|Stáhne dokumenty metadat ze spuštěných služeb.|[Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](./feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|Generuje kód serializace.|[Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí XmlSerializer](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> Svcutil přepíše existující soubory na disku, pokud jsou názvy zadané jako parametry stejné. To může zahrnovat soubory kódu, konfiguraci nebo soubory metadat. Aby k tomu nedocházelo při generování kódu a konfiguračních souborů, použijte `/mergeConfig` přepínač.
>
> Kromě toho `/r` `/ct` přepínače a pro odkazování na typy jsou pro generování kontraktů dat. Tyto přepínače při použití XmlSerializer nefungují.

### <a name="timeout"></a>Časový limit

Při načítání metadat má nástroj časový limit pět minut. Tento časový limit se vztahuje pouze na načítání metadat v síti. Nevztahuje se na zpracování těchto metadat.

### <a name="multi-targeting"></a>Cílení na více platforem

Nástroj nepodporuje cílení na více platforem. Pokud chcete vygenerovat artefakt rozhraní .NET 4 z *svcutil.exe*, použijte *svcutil.exe* ze sady .NET 4 SDK. Chcete-li vygenerovat artefakt rozhraní .NET 3,5, použijte spustitelný soubor ze sady .NET 3,5 SDK.

### <a name="accessing-wsdl-documents"></a>Přístup k dokumentům WSDL

Když použijete Svcutil k přístupu k dokumentu WSDL, který obsahuje odkaz na službu tokenů zabezpečení (STS), Svcutil provede volání WS-MetadataExchange do služby STS. Služba však může zveřejnit své dokumenty WSDL pomocí protokolu WS-MetadataExchange nebo HTTP GET. Pokud tedy služba STS vykázala pouze dokument WSDL pomocí protokolu HTTP GET, klient napsaný v WinFX selže. U klientů napsaných v .NET Framework 3,5 se Svcutil pokusí pomocí protokolu WS-MetadataExchange a HTTP GET získat WSDL pro STS.

## <a name="using-svcutilexe"></a>Použití SvcUtil.exe

### <a name="common-usages"></a>Společná použití

V následující tabulce jsou uvedeny některé běžně používané možnosti pro tento nástroj:

|Možnost|Description|
|------------|-----------------|
|/Directory\<directory>|Adresář, ve kterém se mají vytvářet soubory<br /><br /> Výchozí: aktuální adresář.<br /><br /> Krátký tvar:`/d`|
|/help|Zobrazí syntaxi příkazu a možnosti nástroje.<br /><br /> Krátký tvar:`/?`|
|/noLogo|Potlačíní autorského práva a zprávy banneru.|
|/svcutilConfig:\<configFile>|Určuje vlastní konfigurační soubor, který se použije místo App.config souboru. Tato možnost se dá použít k registraci rozšíření System. serviceModel bez změny konfiguračního souboru nástroje.|
|/Target\<output type>|Určuje výstup, který má nástroj vygenerovat.<br /><br /> Platné hodnoty jsou code, metadata nebo xmlSerializer.<br /><br /> Krátký tvar:`/t`|

### <a name="code-generation"></a>Vytvoření kódu

Svcutil.exe může generovat kód pro kontrakty služeb, klienty a datové typy z dokumentů metadat. Tyto dokumenty metadat mohou být v trvalém úložišti nebo načteny online. Online načítání následuje buď s protokolem WS-Metadata Exchange, nebo s protokolem Disc (podrobnosti najdete v části stažení metadat).

Můžete použít nástroj *SvcUtil.exe* k vygenerování kontraktů služeb a dat na základě předdefinovaného dokumentu WSDL. Použijte přepínač/serviceContract a zadejte adresu URL nebo umístění souboru, kde lze stáhnout nebo najít dokument WSDL. Tím se vygeneruje kontrakt služby a data definovaná v dokumentu WSDL, který pak můžete použít k implementaci služby stížnosti. Další informace naleznete v tématu [How to: načítající metadata a implementující vyhovující služby](./feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).

Pro službu s koncovým bodem třída BasicHttpContextBinding *Svcutil.exe* generuje BasicHttpBinding s `allowCookies` atributem nastaveným na `true` místo. Soubory cookie jsou používány pro kontext na serveru. Pokud chcete spravovat kontext na klientovi, když služba používá soubory cookie, můžete ručně změnit konfiguraci tak, aby používala kontextovou vazbu.

> [!CAUTION]
> Svcutil.exe vygeneruje klienta na základě souboru WSDL nebo zásad obdrženého ze služby. Hlavní název uživatele (UPN) se vygeneruje zřetězením uživatelského jména \@ a plně kvalifikovaného názvu domény (FQDN). Pro uživatele, kteří jsou zaregistrovaní ve službě Active Directory, není tento formát platný a hlavní název uživatele generovaný nástrojem způsobí selhání při ověřování protokolem Kerberos s chybovou zprávou "pokus o přihlášení se nezdařil". Chcete-li tento problém vyřešit, je třeba ručně opravit soubor klienta generovaný tímto nástrojem.

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|Argument|Description|
|--------------|-----------------|
|`epr`|Cesta k souboru XML, který obsahuje WS-Addressing EndpointReference pro koncový bod služby, který podporuje WS-Metadata Exchange. Další informace najdete v části stažení metadat.|
|`metadataDocumentPath`|Cesta k dokumentu metadat (*WSDL* nebo *XSD*), který obsahuje kontrakt pro import do kódu (. WSDL,. xsd,. WSPolicy nebo. wsmex).<br /><br /> Svcutil sleduje import a zahrnuje, když zadáte vzdálenou adresu URL pro metadata. Pokud však chcete zpracovat soubory metadat v místním systému souborů, je nutné zadat všechny soubory v tomto argumentu. Tímto způsobem můžete použít Svcutil v prostředí sestavení, kde nemůžete mít závislosti sítě. Pro tento argument můžete použít zástupné znaky (*. xsd, \* . WSDL).|
|`url`|Adresa URL koncového bodu služby, který poskytuje metadata, nebo k dokumentu metadat hostovanému online. Další informace o tom, jak se tyto dokumenty načítají, najdete v části stažení metadat.|

|Možnost|Description|
|------------|-----------------|
|/async|Generuje synchronní i asynchronní signatury metody.<br /><br /> Výchozí: vygenerujte pouze signatury synchronních metod.<br /><br /> Krátký tvar:`/a`|
|CollectionType\<type>|Určuje typ kolekce seznamu pro klienta WCF.<br/><br /> Výchozí: typ kolekce je System. Array. <br /><br /> Krátký tvar:`/ct`|
|/config\<configFile>|Určuje název souboru pro generovaný konfigurační soubor.<br /><br /> Výchozí: output.config|
|/dataContractOnly|Generuje kód pouze pro typy kontraktu dat. Typy kontraktů služby se nevygenerují.<br /><br /> Pro tuto možnost byste měli zadat jenom místní soubory metadat.<br /><br /> Krátký tvar:`/dconly`|
|/enableDataBinding|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní pro všechny typy kontraktů dat, aby bylo možné datovou vazbu povolit.<br /><br /> Krátký tvar:`/edb`|
|/excludeType:\<type>|Určuje plně kvalifikovaný název nebo kvalifikovaný název sestavení, který bude vyloučen z odkazovaných typů kontraktů.<br /><br /> Při použití tohoto přepínače společně s `/r` z oddělených knihoven DLL je odkazováno na úplný název třídy XSD.<br /><br /> Krátký tvar:`/et`|
|/importXmlTypes|Nakonfiguruje serializátor kontraktu dat pro import typů kontraktů, které nejsou typu data, jako typy IXmlSerializable.|
|/internal|Vygeneruje třídy, které jsou označeny jako interní. Výchozí: vygenerujte pouze veřejné třídy.<br /><br /> Krátký tvar:`/i`|
|/Language\<language>|Určuje programovací jazyk, který se má použít pro generování kódu. Měli byste zadat buď název jazyka zaregistrovaný v souboru Machine.config, nebo plně kvalifikovaný název třídy, která dědí z <xref:System.CodeDom.Compiler.CodeDomProvider> .<br /><br /> Hodnoty: c#, cs, CSharp, VB, VisualBasic, c++, cpp<br /><br /> Výchozí: CSharp<br /><br /> Krátký tvar:`/l`|
|/mergeConfig|Sloučí vygenerovanou konfiguraci do existujícího souboru namísto přepsání stávajícího souboru.|
|/messageContract|Generuje typy kontraktů zpráv.<br /><br /> Krátký tvar:`/mc`|
|/Namespace\<string,string>|Určuje mapování z oboru názvů targetNamespace schématu WSDL nebo XML na obor názvů CLR. Použití \* atributu pro obor názvů targetNamespace mapuje všechny obory názvů targetNamespace bez explicitního mapování na tento obor názvů CLR.<br /><br /> Aby se zajistilo, že název kontraktu zprávy nekoliduje s názvem operace, měli byste buď kvalifikovat odkaz na typ `::` , nebo se ujistit, že jsou názvy jedinečné.<br /><br /> Výchozí: odvozeno z cílového oboru názvů dokumentu schématu pro kontrakty dat. Výchozí obor názvů se používá pro všechny ostatní generované typy.<br /><br /> Krátký tvar: `/n` **Poznámka:** při generování typů pro použití s objektem XmlSerializer je podporována pouze mapování jednoho oboru názvů. Všechny generované typy budou buď ve výchozím oboru názvů, nebo v oboru názvů určeném hvězdičkou (*).|
|/noConfig|Negenerovat konfigurační soubory.|
|/noStdLib|Neodkazujte na standardní knihovny.<br /><br /> Výchozí: odkazují na Mscorlib.dll a System.servicemodel.dll.|
|/out\<file>|Určuje název souboru generovaného kódu.<br /><br /> Výchozí: odvozeno z názvu definice WSDL, název služby WSDL nebo cílový obor názvů jednoho ze schémat.<br /><br /> Krátký tvar:`/o`|
|/Reference\<file path>|Odkazuje na typy v zadaném sestavení. Při generování klientů pomocí této možnosti zadejte sestavení, která mohou obsahovat typy představující importovaná metadata.<br /><br /> Pomocí tohoto přepínače nelze zadat kontrakty a <xref:System.Xml.Serialization.XmlSerializer> typy zpráv.<br /><br /> <xref:System.DateTimeOffset>Je-li odkazováno, tento typ je použit místo generování nového typu. Pokud je aplikace napsaná pomocí .NET Framework 3,5, SvcUtil.exe se automaticky odkazuje na ně <xref:System.DateTimeOffset> .<br /><br /> Krátký tvar:`/r`|
|/serializable|Generuje třídy označené serializovatelným atributem.<br /><br /> Krátký tvar:`/s`|
|/serviceContract|Vygenerujte pouze kód pro kontrakty služeb. Třída klienta a konfigurace nebudou vygenerovány.<br /><br /> Krátký tvar:`/sc`|
|/Serializer: auto|Automatický výběr serializátoru. Tato operace se pokusí použít serializátor kontraktu dat a v případě, že dojde k chybě, použije XmlSerializer.<br /><br /> Krátký tvar:`/ser`|
|/Serializer: DataContractSerializer|Generuje datové typy, které používají serializátor kontraktu dat pro serializaci a deserializaci.<br /><br /> Krátký tvar:`/ser:DataContractSerializer`|
|/Serializer: XmlSerializer|Generuje datové typy, které používají <xref:System.Xml.Serialization.XmlSerializer> pro serializaci a deserializaci.<br /><br /> Krátký tvar:`/ser:XmlSerializer`|
|/targetClientVersion|Určete, na kterou verzi .NET Framework aplikace cílí. Platné hodnoty jsou `Version30` a `Version35` . Výchozí hodnota je `Version30`.<br /><br /> Krátký tvar:`/tcv`<br /><br /> `Version30`: Použijte `/tcv:Version30` , pokud generujete kód pro klienty, kteří používají WinFX.<br /><br /> `Version35`: Použijte `/tcv:Version35` , pokud generujete kód pro klienty, kteří používají .NET Framework 3,5. Při použití `/tcv:Version35` s `/async` přepínačem jsou vygenerovány asynchronní metody založené na událostech a zpětném volání nebo delegátem. Kromě toho je podpora pro datové sady s podporou LINQ a <xref:System.DateTimeOffset> povolená.|
|/wrapped|Určuje, zda se pro dokumenty se stylem literálu dokumentu s zabalením parametrů používá speciální velikost písmen. K určení normálního malých a velkých písmen použijte přepínač **/Wrapped** s nástrojem [Service model metadat Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) .|

> [!NOTE]
> Je-li vazba služby jednou z uživatelsky definovaných vazeb (viz [systémové vazby](system-provided-bindings.md)) a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost je nastavena na hodnotu `None` nebo `Sign` , Svcutil vygeneruje konfigurační soubor pomocí [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) elementu namísto očekávaného prvku poskytnutého systémem. Například pokud služba používá `<wsHttpBinding>` prvek s `ProtectionLevel` nastavením na `Sign` , vygenerovaná konfigurace má `<customBinding>` v části Bindings místo `<wsHttpBinding>` . Další informace o úrovni ochrany najdete v tématu [Principy úrovně ochrany](understanding-protection-level.md).

### <a name="metadata-export"></a>Export metadat

Svcutil.exe může exportovat metadata pro služby, kontrakty a datové typy v kompilovaných sestaveních. Pokud chcete exportovat metadata pro službu, musíte použít `/serviceName` možnost k zadání služby, kterou chcete exportovat. Chcete-li exportovat všechny typy kontraktů dat v rámci sestavení, měli byste použít `/dataContractOnly` možnost. Ve výchozím nastavení se metadata exportují pro všechny kontrakty služeb ve vstupních sestaveních.

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|Argument|Description|
|--------------|-----------------|
|`assemblyPath`|Určuje cestu k sestavení, které obsahuje služby, kontrakty nebo typy kontraktů dat, které mají být exportovány. Standardní zástupné znaky příkazového řádku je možné použít k zadání několika souborů jako vstupu.|

|Možnost|Description|
|------------|-----------------|
|ServiceName\<serviceConfigName>|Určuje název konfigurace služby, která se má exportovat. Pokud použijete tuto možnost, musí se jako vstup předat spustitelné sestavení s přidruženým konfiguračním souborem. Svcutil.exe vyhledá všechny přidružené konfigurační soubory pro konfiguraci služby. Pokud konfigurační soubory obsahují jakékoli typy rozšíření, sestavení, která obsahují tyto typy, musí být buď v globální mezipaměti sestavení (GAC), nebo musí být explicitně poskytnuta pomocí `/reference` Možnosti.|
|/Reference\<file path>|Přidá zadané sestavení do sady sestavení používané pro překlad odkazů typu. Pokud exportujete nebo ověřujete službu, která používá rozšíření třetích stran (chování, vazby a BindingElements) zaregistrovaná v konfiguraci, použijte tuto možnost k vyhledání sestavení rozšíření, která nejsou v globální mezipaměti sestavení (GAC).<br /><br /> Krátký tvar:`/r`|
|/dataContractOnly|Funguje pouze na typech kontraktů dat. Kontrakty služby se nezpracovávají.<br /><br /> Pro tuto možnost byste měli zadat jenom místní soubory metadat.<br /><br /> Krátký tvar:`/dconly`|
|/excludeType:\<type>|Určuje plně kvalifikovaný název nebo kvalifikovaný název sestavení typu, který se má vyloučit z exportu. Tuto možnost lze použít při exportu metadat pro službu nebo sadu kontraktů služby pro vyloučení typů z exportu. Tuto možnost nelze použít společně s `/dconly` možností.<br /><br /> Pokud máte jedno sestavení obsahující několik služeb a každá z nich používá samostatné třídy se stejným názvem XSD, měli byste pro tento přepínač zadat název služby místo názvu třídy XSD.<br /><br /> Typy XSD nebo kontraktů dat nejsou podporovány.<br /><br /> Krátký tvar:`/et`|

### <a name="service-validation"></a>Ověření služby

Ověřování lze použít k detekci chyb v implementacích služby bez hostování služby. Je nutné použít `/serviceName` možnost k označení služby, kterou chcete ověřit.

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|Argument|Description|
|--------------|-----------------|
|`assemblyPath`|Určuje cestu k sestavení, které obsahuje typy služby, které mají být ověřeny. Sestavení musí mít přidružený konfigurační soubor pro zajištění konfigurace služby. Standardní zástupné znaky příkazového řádku lze použít k poskytnutí více sestavení.|

|Možnost|Description|
|------------|-----------------|
|/Validate|Ověří implementaci služby určenou `/serviceName` možností. Pokud použijete tuto možnost, musí se jako vstup předat spustitelné sestavení s přidruženým konfiguračním souborem.<br /><br /> Krátký tvar:`/v`|
|ServiceName\<serviceConfigName>|Určuje název konfigurace služby, která se má ověřit. Svcutil.exe vyhledá všechny přidružené konfigurační soubory všech vstupních sestavení pro konfiguraci služby. Pokud konfigurační soubory obsahují jakékoli typy rozšíření, sestavení, která obsahují tyto typy, musí být buď v globální mezipaměti sestavení (GAC), nebo musí být explicitně poskytnuta pomocí `/reference` Možnosti.|
|/Reference\<file path>|Přidá zadané sestavení do sady sestavení používané pro překlad odkazů typu. Pokud exportujete nebo ověřujete službu, která používá rozšíření třetích stran (chování, vazby a BindingElements) zaregistrovaná v konfiguraci, použijte tuto možnost k vyhledání sestavení rozšíření, která nejsou v globální mezipaměti sestavení (GAC).<br /><br /> Krátký tvar:`/r`|
|/dataContractOnly|Funguje pouze na typech kontraktů dat. Kontrakty služby se nezpracovávají.<br /><br /> Pro tuto možnost byste měli zadat jenom místní soubory metadat.<br /><br /> Krátký tvar:`/dconly`|
|/excludeType:\<type>|Určuje plně kvalifikovaný název nebo kvalifikovaný název sestavení typu, který se má vyloučit z ověřování.<br /><br /> Krátký tvar:`/et`|

### <a name="metadata-download"></a>Stažení metadat

Svcutil.exe lze použít ke stažení metadat ze spuštěných služeb a k uložení metadat do místních souborů. Chcete-li stáhnout metadata, je nutné zadat `/t:metadata` možnost. V opačném případě se generuje kód klienta. V případě schémat URL protokolu HTTP a HTTPS se Svcutil.exe pokusí načíst metadata pomocí WS-Metadata Exchange a DISCového systému. Pro všechna ostatní schémata URL Svcutil.exe používá pouze WS-Metadata Exchange.

Svcutil vyžádá současně následující požadavky metadat pro načtení metadat.

- Požadavek MEX (WS-Transfer) na zadanou adresu

- Požadavek MEX na zadanou adresu s připojením/MEX

- Požadavek na DISCích (pomocí DiscoveryClientProtocol z ASMX) na zadanou adresu.

Ve výchozím nastavení Svcutil.exe používá vazby definované ve <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídě k vytváření požadavků MEX. Ke konfiguraci vazby používaného pro WS-Metadata Exchange musíte v konfiguraci, která používá kontrakt IMetadataExchange, definovat koncový bod klienta. To lze definovat buď v konfiguračním souboru Svcutil.exe, nebo v jiném konfiguračním souboru zadaném pomocí `/svcutilConfig` Možnosti.

`svcutil.exe /t:metadata  <url>* | <epr>`

|Argument|Description|
|--------------|-----------------|
|`url`|Adresa URL koncového bodu služby, který poskytuje metadata, nebo k dokumentu metadat hostovanému online.|
|`epr`|Cesta k souboru XML, který obsahuje WS-Addressing EndpointReference pro koncový bod služby, který podporuje WS-Metadata Exchange.|

### <a name="xmlserializer-type-generation"></a>Generování typu XmlSerializer

Služby a klientské aplikace, které používají datové typy, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilování serializace kódu pro tyto datové typy za běhu, což může vést k pomalému spuštění výkonu.

> [!NOTE]
> Předem generovaný kód serializace lze použít pouze v klientských aplikacích, nikoli v službách.

Svcutil.exe může vygenerovat nezbytný kód serializace v jazyce C# z kompilovaných sestavení pro aplikaci, čímž se zvyšuje výkon při spuštění těchto aplikací. Další informace naleznete v tématu [How to: vylepšení doby spouštění klientských aplikací WCF pomocí objektu XmlSerializer](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

> [!NOTE]
> Svcutil.exe generuje pouze kód pro typy používané kontrakty služby nalezenými ve vstupních sestaveních.

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|Argument|Description|
|--------------|-----------------|
|`assemblyPath`|Určuje cestu k sestavení, které obsahuje typy kontraktů služby. Typy serializace jsou generovány pro všechny Serializovatelné typy XML v každé kontraktu.|

|Možnost|Description|
|------------|-----------------|
|/Reference\<file path>|Přidá zadané sestavení do sady sestavení používané pro překlad odkazů typu.<br /><br /> Krátký tvar:`/r`|
|/excludeType:\<type>|Určuje plně kvalifikovaný název nebo kvalifikovaný název sestavení typu, který se má vyloučit z exportu nebo ověřování.<br /><br /> Krátký tvar:`/et`|
|/out\<file>|Určuje název souboru pro vygenerovaný kód. Tato možnost je ignorována, pokud je do nástroje předána více sestavení jako vstup.<br /><br /> Výchozí: odvozeno z názvu sestavení.<br /><br /> Krátký tvar:`/o`|
|/UseSerializerForFaults|Určuje, že se <xref:System.Xml.Serialization.XmlSerializer> má použít pro čtení a zápis chyb namísto výchozí hodnoty <xref:System.Runtime.Serialization.DataContractSerializer> .|

## <a name="examples"></a>Příklady

Následující příkaz vygeneruje kód klienta ze spuštěné služby nebo online dokumentů metadat.

`svcutil http://service/metadataEndpoint`

Následující příkaz vygeneruje kód klienta z místních dokumentů metadat.

`svcutil *.wsdl *.xsd /language:C#`

Následující příkaz generuje typy kontraktů dat v Visual Basic z místních dokumentů schématu.

`svcutil /dconly *.xsd /language:VB`

Následující příkaz stáhne dokumenty metadat ze spuštěných služeb.

`svcutil /t:metadata http://service/metadataEndpoint`

Následující příkaz generuje dokumenty metadat pro kontrakty služby a přidružené typy v sestavení.

`svcutil myAssembly.dll`

Následující příkaz generuje dokumenty metadat pro službu a všechny přidružené kontrakty služby a datové typy v sestavení.

`svcutil myServiceHost.exe /serviceName:myServiceName`

Následující příkaz generuje dokumenty metadat pro datové typy v sestavení.

`svcutil myServiceHost.exe /dconly`

Následující příkaz ověří hostování služby.

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

Následující příkaz generuje typy serializace pro <xref:System.Xml.Serialization.XmlSerializer> typy používané všemi kontrakty služby v sestavení.

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>Maximální kvóta počtu NameTable znaků

Při použití Svcutil ke generování metadat pro službu se může zobrazit následující zpráva:

Chyba: Nepodařilo se získat metadata z `http://localhost:8000/somesservice/mex` maximální kvóty počtu znaků NameTable (16384), která byla při čtení dat XML překročena. NameTable je datová struktura, která se používá k ukládání řetězců zjištěných během zpracování XML – dlouhé dokumenty XML s názvy elementů, které nejsou opakující se, názvy atributů a hodnoty atributů můžou tuto kvótu aktivovat. Tato kvóta se dá zvýšit změnou vlastnosti MaxNameTableCharCount u objektu XmlDictionaryReaderQuotas, který se používá při vytváření čtecího modulu XML.

Tato chyba může být způsobena službou, která vrací velký soubor WSDL při žádosti o jeho metadata. Problém je, že se překročila kvóta znaků pro nástroj svcutil.exe. Tato hodnota je nastavená tak, aby bránila útokům DOS (Denial of Service). Tuto kvótu můžete zvýšit zadáním následujícího konfiguračního souboru pro Svcutil.

Následující konfigurační soubor ukazuje, jak nastavit kvóty čtecího modulu pro Svcutil.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <customBinding>
                <binding name="MyBinding">
                    <textMessageEncoding>
                        <readerQuotas maxDepth="2147483647" maxStringContentLength="2147483647"
                            maxArrayLength="2147483647" maxBytesPerRead="2147483647" maxNameTableCharCount="2147483647" />
                    </textMessageEncoding>
                    <httpTransport maxReceivedMessageSize="2147483647" maxBufferSize="2147483647" />
                </binding>
            </customBinding>
        </bindings>
        <client>
            <endpoint binding="customBinding" bindingConfiguration="MyBinding"
                contract="IMetadataExchange"
                name="http" />
        </client>
    </system.serviceModel>
</configuration>
```

Vytvořte nový soubor s názvem svcutil.exe.config a zkopírujte do něj ukázkový kód XML. Pak soubor umístěte do stejného adresáře jako svcutil.exe. Při příštím svcutil.exe se spustí nová nastavení.

## <a name="security-concerns"></a>Problematika zabezpečení

K ochraně instalační složky Svcutil.exe, Svcutil.config a souborů, na které odkazuje, byste měli použít příslušný seznam Access Control (ACL) `/svcutilConfig` . To může zabránit v registraci a spuštění škodlivých rozšíření.

Kromě toho pro minimalizaci pravděpodobnosti ohrožení zabezpečení byste neměli přidat nedůvěryhodná rozšíření, aby byla součástí systému, nebo používat nedůvěryhodné poskytovatele kódů s Svcutil.exe.

Nakonec byste neměli používat nástroj v prostřední vrstvě aplikace, protože může způsobit odepření služby pro aktuální proces.

## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Postupy: Vytvoření klienta](how-to-create-a-wcf-client.md)
