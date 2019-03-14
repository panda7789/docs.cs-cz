---
title: Nástroj ServiceModel Metadata Utility (Svcutil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 02b1b0f6215f7d26974a8e1e58fbefbb5d159cf7
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788424"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>Nástroj ServiceModel Metadata Utility (Svcutil.exe)

Nástroj ServiceModel Metadata Utility slouží ke generování kódu modelu služby z dokumentů metadat a dokumentů metadat z modelu kódu služby.

## <a name="svcutilexe"></a>SvcUtil.exe

Nástroj ServiceModel Metadata Utility najdete v umístění instalace sady Windows SDK, konkrétně *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin*.

### <a name="functionalities"></a>Funkce

Následující tabulka shrnuje různé funkce tak, že tento nástroj a příslušné téma, který popisuje, jak se používají k dispozici:

|Úloha|Téma|
|----------|-----------|
|Generuje kód ze spuštěné služby nebo statických dokumentů metadat.|[Generování klienta WCF z metadat služby](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|
|Exportuje dokumentů metadat z kompilovaného kódu.|[Postupy: Použití Svcutil.exe pro Export metadat z kompilovaného kódu služby](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|Ověří kompilovaného kódu služby.|[Postupy: Pomocí Svcutil.exe k ověření zkompilovaného kódu služby](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|Soubory ke stažení dokumentů metadat od spuštění služby.|[Postupy: Stažení dokumentů metadat pomocí Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|Generuje kód serializace.|[Postupy: Vylepšení spuštění čas z klientských aplikací WCF pomocí třídy XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> Svcutil přepíše existující soubory na disku, pokud jsou identické názvy zadané jako parametry. To může zahrnovat soubory kódu, konfigurace nebo soubory metadat. Chcete-li předejít při generování kódu a konfigurační soubory, použijte `/mergeConfig` přepnout.
>
> Kromě toho `/r` a `/ct` přepínače pro odkazování na typy jsou určeny pro vygenerování kontraktů dat. Tyto přepínače nefungují při používání třídy XmlSerializer.

### <a name="timeout"></a>časový limit

Nástroj má časový limit 5 minut při načítání metadat. Tento časový limit platí jenom pro načítání metadat přes síť. Nevztahuje se na zpracování těchto metadat.

### <a name="multi-targeting"></a>Cílení na více platforem

Nástroj nepodporuje cílení na více platforem. Pokud chcete generovat .NET 4 artefaktů z *svcutil.exe*, použijte *svcutil.exe* ze sady SDK rozhraní .NET 4. Ke generování artefaktu .NET 3.5, pomocí spustitelného souboru z .NET 3.5 SDK.

### <a name="accessing-wsdl-documents"></a>Přístup k dokumenty WSDL

Pokud používáte nástroj Svcutil pro přístup k dokumentu WSDL, který obsahuje odkaz na službu tokenů zabezpečení (STS), Svcutil díky WS-MetadataExchange volání na službu STS. Služba však můžete zveřejnit své dokumenty WSDL přes WS-MetadataExchange nebo HTTP GET. Proto pokud služba tokenů zabezpečení je dostupná jenom v případě použití HTTP GET klienta napsané v dokumentu WSDL [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] se nezdaří. Pro klienty v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]Svcutil pokusí použít obě WS-MetadataExchange a HTTP GET získat WSDL služby tokenů zabezpečení.

## <a name="using-svcutilexe"></a>Pomocí SvcUtil.exe

### <a name="common-usages"></a>Běžné použití

V následující tabulce jsou uvedeny některé běžně používané možnosti pro tento nástroj:

|Možnost|Popis|
|------------|-----------------|
|/ directory:\<adresáře >|Adresář, které mají být vytvořeny soubory.<br /><br /> Výchozí hodnota: Aktuální adresář.<br /><br /> Krátký tvar: `/d`|
|/help|Zobrazí syntaxi příkazu a možnosti nástroje.<br /><br /> Krátký tvar: `/?`|
|/noLogo|Potlačí zprávu o autorských právech a úvodní nápis.|
|/svcutilConfig:\<configFile>|Určuje vlastní konfigurační soubor, který chcete použít místo souboru App.config. To lze použít k registraci rozšíření system.serviceModel beze změny konfiguračního souboru nástroje.|
|/ target:\<výstupní typ >|Určuje výstup, který byl vygenerován nástrojem nástroj.<br /><br /> Platné hodnoty jsou kódu, metadata nebo xmlSerializer.<br /><br /> Krátký tvar: `/t`|

### <a name="code-generation"></a>Vytvoření kódu

Svcutil.exe lze generovat kód pro typy kontraktů, klientů a dat služby z dokumentů metadat. Tyto dokumenty metadat mohou být odolné úložiště nebo načítá online. Načítání online následuje protokol WS-Metadata Exchange nebo protokol Roz (podrobné informace najdete v části stáhnout Metadata).

Můžete použít *SvcUtil.exe* nástroj generovat kontrakty služby a dat na základě předdefinovaných dokumentu WSDL. Použijte přepínač /serviceContract a zadejte adresu URL nebo soubor umístění, kam dokument WSDL si můžete stáhnout nebo najít. Tím se vygeneruje kontrakty služby a data definovaný v dokumentu WSDL, který lze použít k implementaci služby předpisy. Další informace najdete v tématu [jak: Načítání metadat a implementace kompatibilní služby](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).

Pro službu s koncovým bodem třída BasicHttpContextBinding *Svcutil.exe* generuje BasicHttpBinding s `allowCookies` atribut nastaven na `true` místo. Soubory cookie se používají pro kontext na serveru. Pokud chcete ke správě kontextu na straně klienta, pokud služba používá soubory cookie, můžete ručně upravit konfigurace, aby používala kontextu vazby.

> [!CAUTION]
> Svcutil.exe generuje klienta na základě souboru WSDL nebo zásad přijatých ze služby. Hlavní název uživatele (UPN) je generována zřetězením uživatelské jméno, "\@" a plně kvalifikovaný název domény (FQDN). Pro uživatele, kteří si zaregistrovali ve službě Active Directory, ale tento formát není platný a hlavní název uživatele generovaný nástrojem způsobí, že k chybě v ověřování protokolem Kerberos s chybovou zprávou "Pokus o přihlášení se nezdařilo". Chcete-li vyřešit tento problém, by měla vyřešit ručně instalační soubor klienta generované tímto nástrojem.

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|Argument|Popis|
|--------------|-----------------|
|`epr`|Cesta k souboru XML, který obsahuje WS-Addressing EndpointReference pro koncový bod služby podporující WS-Metadata Exchange. Další informace najdete v části stáhnout Metadata.|
|`metadataDocumentPath`|Cesta k dokumentu metadat (*wsdl* nebo *xsd*), který obsahuje smlouvu pro import do kódu (WSDL, XSD, .wspolicy nebo .wsmex).<br /><br /> Svcutil následující importy a zahrnuje při zadávání vzdálenou adresu URL pro metadata. Pokud chcete zpracovat soubory metadat v místním systému souborů, je tento argument musíte zadat všechny soubory. Tímto způsobem můžete použít nástroj Svcutil v prostředí sestavení kde nemůže mít síťové závislosti. Můžete použít zástupné znaky (*.xsd, \*WSDL) pro tento argument.|
|`url`|Adresa URL koncového bodu služby, která poskytuje metadata nebo k dokumentu metadat hostované online. Další informace o tom, jak tyto dokumenty se načítají najdete v části stáhnout Metadata.|

|Možnost|Popis|
|------------|-----------------|
|/Async|Generuje obou podpisy synchronní i asynchronní metody.<br /><br /> Výchozí: generovat pouze podpisy synchronní metody.<br /><br /> Krátký tvar: `/a`|
|/collectionType:\<typ >|Určuje typ kolekce seznamu pro klienta WCF.<br/><br /> Výchozí hodnota: typ kolekce je System.Array. <br /><br /> Krátký tvar: `/ct`|
|/config:\<configFile>|Určuje název souboru pro vygenerovaný konfiguračního souboru.<br /><br /> Výchozí: output.config|
|/dataContractOnly|Generuje kód pro typy kontraktů dat pouze. Nejsou generované typy kontraktů služby.<br /><br /> Měli byste zadat pouze soubory místních metadat pro tuto možnost.<br /><br /> Krátký tvar: `/dconly`|
|/enableDataBinding|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní na všechny typy kontraktu dat. Chcete-li vytvořit datovou vazbu.<br /><br /> Krátký tvar: `/edb`|
|/excludeType:\<typ >|Určuje název plně kvalifikovaný nebo sestavením kvalifikovaný typ mají být vyloučeny z smlouvy odkazované typy.<br /><br /> Při použití tohoto parametru spolu s `/r` ze samostatné knihovny DLL, se odkazuje úplný název třídy XSD.<br /><br /> Krátký tvar: `/et`|
|/importXmlTypes|Nakonfiguruje serializátor kontraktu dat. není pro import kontraktu dat typy jako typy rozhraní IXmlSerializable.|
|/ interní|Vygeneruje třídy, které jsou označeny jako vnitřní. Výchozí: generovat veřejné třídy pouze.<br /><br /> Krátký tvar: `/i`|
|/Language:\<jazyk >|Určuje programovací jazyk, který má použít pro generování kódu. By měla poskytnout buď název jazyka zaregistrovaný v souboru Machine.config, nebo plně kvalifikovaný název třídy, která dědí z <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Hodnoty: c#, cs, csharp, vb, visualbasic, c ++, cpp<br /><br /> Výchozí: csharp<br /><br /> Krátký tvar: `/l`|
|/mergeConfig|Sloučí existující soubor, místo abyste přepsali tu stávající soubor vygenerovanou konfiguraci.|
|/messageContract|Generuje typy kontraktů zpráv.<br /><br /> Krátký tvar: `/mc`|
|/ NAMESPACE:\<string, string >|Určuje mapování z targetNamespace schématu WSDL nebo XML na názvový prostor CLR. Použití "\*" pro targetNamespace bez explicitního mapování všech lze mapovat na tento obor názvů CLR.<br /><br /> Pokud chcete mít jistotu, že název kontraktu zprávy nejsou v konfliktu s názvem operace, by měly buď kvalifikovat odkaz na typ s `::`, nebo se ujistěte, názvy musí být jedinečné.<br /><br /> Výchozí hodnota: Odvozenou z cílového oboru názvů dokumentu schématu pro kontrakty dat. Výchozí obor názvů je používán pro všechny ostatní generované typy.<br /><br /> Krátký tvar: `/n` **Poznámka:**  Při generování typů pro použití s pomocí třídy XmlSerializer, se podporuje jenom mapování jednoho oboru názvů. Všechny typy generovaného bude buď ve výchozí obor názvů nebo oboru názvů určeném "*".|
|/noConfig|Konfigurační soubory nejsou generovány.|
|/noStdLib|Neodkazovat na standardní knihovny.<br /><br /> Výchozí hodnota: Soubor mscorlib.dll a System.servicemodel.dll odkazují.|
|/ out:\<souboru >|Určuje název souboru pro vygenerovaný kód.<br /><br /> Výchozí hodnota: WSDL odvozeno z názvu definice WSDL, název služby nebo cílový obor názvů jednoho ze schémat.<br /><br /> Krátký tvar: `/o`|
|/ reference:\<cesta k souboru >|Typy odkazů v zadaném sestavení. Při generování klientů, pokud pomocí této možnosti zadejte sestavení, která může obsahovat typy představující importovaná metadata.<br /><br /> Nelze zadat kontraktů zpráv a <xref:System.Xml.Serialization.XmlSerializer> typy pomocí tohoto přepínače.<br /><br /> Pokud <xref:System.DateTimeOffset> odkazuje, tento typ se používá místo generování nového typu. Pokud aplikace je zapsáno s použitím [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], odkazy SvcUtil.exe <xref:System.DateTimeOffset> automaticky.<br /><br /> Krátký tvar: `/r`|
|/ serializovatelný|Vygeneruje třídy označené atributem serializovatelný.<br /><br /> Krátký tvar: `/s`|
|/serviceContract|Generování kódu pro pouze kontraktů služby. Třída klienta a konfigurace nebude vytvořen<br /><br /> Krátký tvar: `/sc`|
|/serializer:Auto|Automatický výběr serializátoru. To se pokusí použít serializátor kontraktu dat. není a používá XmlSerializer, pokud se nezdaří.<br /><br /> Krátký tvar: `/ser`|
|/serializer:DataContractSerializer|Datové typy, které k serializaci a deserializaci používají serializátor kontraktu dat generuje.<br /><br /> Krátký tvar: `/ser:DataContractSerializer`|
|/serializer:XmlSerializer|Generuje datové typy, které používají <xref:System.Xml.Serialization.XmlSerializer> k serializaci a deserializaci.<br /><br /> Krátký tvar: `/ser:XmlSerializer`|
|/targetClientVersion|Určit používanou verzi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] cílení aplikace. Platné hodnoty jsou `Version30` a `Version35`. Výchozí hodnota je `Version30`.<br /><br /> Krátký tvar: `/tcv`<br /><br /> `Version30`: Použít `/tcv:Version30` Pokud jsou generování kódu pro klienty, kteří používají [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].<br /><br /> `Version35`: Použít `/tcv:Version35` Pokud jsou generování kódu pro klienty, kteří používají [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Při použití `/tcv:Version35` s `/async` přepnout, obě založený na událostech a jsou generovány založený/zpětného volání asynchronní metody. Kromě toho podporují podporující LINQ datových sad a <xref:System.DateTimeOffset> je povolená.|
|/ zabalené|Určuje, zda zvláštní případy se používá pro literál dokumentu ve stylu dokumenty s zabalené parametry. Použití **/ zabalené** přepněte se [Service Model metadat Tool Utility (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro určení normální velká a malá písmena.|

> [!NOTE]
> Když vazby služby je jedna z vazeb poskytovaných systémem (naleznete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md)) a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> je nastavena na hodnotu `None` nebo `Sign`, Svcutil generuje konfiguračním souboru pomocí [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu namísto očekávaného elementu poskytované systémem. Například, pokud služba používá `<wsHttpBinding>` element s `ProtectionLevel` nastavena na `Sign`, vygenerované konfigurace má `<customBinding>` v části vazeb místo `<wsHttpBinding>`. Další informace o úroveň ochrany, naleznete v tématu [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md).

### <a name="metadata-export"></a>Export metadat

Svcutil.exe lze exportovat metadata pro služby, kontrakty a datové typy v kompilovaných sestavení. Pro export metadat pro službu, je nutné použít `/serviceName` možnost určení služby, který chcete exportovat. Chcete-li exportovat všechny typy kontraktu dat v rámci sestavení, měli byste použít `/dataContractOnly` možnost. Ve výchozím nastavení metadata exportu pro všechny kontrakty služeb ve vstupní sestavení.

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|Argument|Popis|
|--------------|-----------------|
|`assemblyPath`|Určuje cestu k sestavení, který obsahuje typy kontraktů služby, kontrakty nebo data nelze exportovat. Zástupné znaky příkazového řádku standardní slouží k poskytování více souborů, jako vstup.|

|Možnost|Popis|
|------------|-----------------|
|/serviceName:\<serviceConfigName>|Určuje název konfigurace služby nelze exportovat. Pokud tato možnost se používá, spustitelného sestavení s související konfigurační soubor musí být předán jako vstup. Svcutil.exe vyhledá všechny přidružené konfigurační soubory pro konfiguraci služby. Pokud konfigurační soubory obsahují všechny typy rozšíření, sestavení, které obsahují tyto typy musí být buď v mezipaměti GAC, nebo explicitně zadat pomocí `/reference` možnost.|
|/ reference:\<cesta k souboru >|Přidá zadané sestavení na sadu sestavení, které používá k vyřešení odkazů na typy. Pokud exportujete nebo služba, která používá rozšíření 3rd třetích stran (chování, vazby a tříd BindingElements) zaregistrovaný v konfiguraci ověřování pomocí této možnosti můžete najít sestavení rozšíření, které nejsou v mezipaměti GAC.<br /><br /> Krátký tvar: `/r`|
|/dataContractOnly|Pracuje s daty pouze typy kontraktů. Kontrakty služeb nebudou zpracovány.<br /><br /> Měli byste zadat pouze soubory místních metadat pro tuto možnost.<br /><br /> Krátký tvar: `/dconly`|
|/excludeType:\<typ >|Určuje plně kvalifikovaný nebo sestavením kvalifikovaný název typu, které se mají vyloučit z exportu. Tato možnost se dá použít při exportu metadat pro službu nebo sadu service smluv týkajících se můžete vyloučit typy exportování. Tuto možnost nelze použít společně s `/dconly` možnost.<br /><br /> Pokud máte jednoho sestavení obsahující více služeb, a každý využívá samostatné třídy se stejným názvem XSD, měli byste určit název služby místo názvu třídy XSD pro tento přepínač.<br /><br /> XSD nebo datovými typy kontraktů nejsou podporovány.<br /><br /> Krátký tvar: `/et`|

### <a name="service-validation"></a>Ověření služby

Ověření lze použít ke zjištění chyby v implementacích služby bez, který je hostitelem služby. Je nutné použít `/serviceName` možnost k označení službu, kterou chcete ověřit.

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|Argument|Popis|
|--------------|-----------------|
|`assemblyPath`|Určuje cestu k sestavení, který obsahuje typy služeb, které má být ověřen. Sestavení musí mít přidružený konfiguračního souboru a zadejte konfiguraci služby. Standardní zástupné znaky příkazového řádku je možné poskytnout více sestavení.|

|Možnost|Popis|
|------------|-----------------|
|/ validate|Ověří implementace služby určené `/serviceName` možnost. Pokud tato možnost se používá, spustitelného sestavení s související konfigurační soubor musí být předán jako vstup.<br /><br /> Krátký tvar: `/v`|
|/serviceName:\<serviceConfigName>|Určuje název konfigurace služby, který má být ověřen. Svcutil.exe vyhledá všechny přidružené konfigurační soubory všechny vstupní sestavení pro konfiguraci služby. Pokud konfigurační soubory obsahují všechny typy rozšíření, sestavení, která obsahuje tyto typy musí být buď v mezipaměti GAC, nebo explicitně zadat pomocí `/reference` možnost.|
|/ reference:\<cesta k souboru >|Přidá zadané sestavení na sadu sestavení, které používá k vyřešení odkazů na typy. Pokud exportujete nebo služba, která používá rozšíření 3rd třetích stran (chování, vazby a tříd BindingElements) zaregistrovaný v konfiguraci ověřování pomocí této možnosti můžete najít sestavení rozšíření, které nejsou v mezipaměti GAC.<br /><br /> Krátký tvar: `/r`|
|/dataContractOnly|Pracuje s daty pouze typy kontraktů. Kontrakty služeb nebudou zpracovány.<br /><br /> Měli byste zadat pouze soubory místních metadat pro tuto možnost.<br /><br /> Krátký tvar: `/dconly`|
|/excludeType:\<typ >|Určuje plně kvalifikovaný nebo sestavením kvalifikovaný název typu, které se mají vyloučit z ověření.<br /><br /> Krátký tvar: `/et`|

### <a name="metadata-download"></a>Stažení metadat

Svcutil.exe lze použít ke stažení metadat z službami a uložit metadata do místních souborů. Pokud chcete stáhnout metadata, je nutné zadat `/t:metadata` možnost. V opačném případě je vygenerován kód klienta. Pro schémata HTTP a HTTPS URL pokusí Svcutil.exe k načtení metadat pomocí protokolu WS-Metadata Exchange a roz. Pro všechny ostatní schémata URL Svcutil.exe využívá jenom WS-Metadata Exchange.

Svcutil problémy s následujícími požadavky metadat současně k načtení metadat.

- MEX (WS-přenos) žádost o zadané adresy

- MEX požadavek na zadané adresy s /mex připojeno

- DISCO požadavku (s použitím DiscoveryClientProtocol z ASMX) na zadané adresy.

Ve výchozím nastavení používá Svcutil.exe vazeb definovaných v <xref:System.ServiceModel.Description.MetadataExchangeBindings> třídy, aby MEX požadavků. Ke konfiguraci vazby používá pro WS-Metadata Exchange, je nutné definovat koncový bod klienta v konfiguraci, která používá kontraktu IMetadataExchange. To mohou být definovány v konfiguračním souboru Svcutil.exe nebo v jiném souboru konfigurace zadat pomocí `/svcutilConfig` možnost.

`svcutil.exe /t:metadata  <url>* | <epr>`

|Argument|Popis|
|--------------|-----------------|
|`url`|Adresa URL koncového bodu služby, která poskytuje metadata nebo k dokumentu metadat hostované online.|
|`epr`|Cesta k souboru XML, který obsahuje WS-Addressing EndpointReference pro koncový bod služby podporující WS-Metadata Exchange.|

### <a name="xmlserializer-type-generation"></a>Generování typů třídy XmlSerializer

Služby a klientské aplikace, které používají datové typy, které jsou serializovatelné pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilaci kódu serializace pro typy dat za běhu, což může vést k pomalé spouštění výkonu.

> [!NOTE]
> Předem generovaného Serializační kód jde použít jenom v klientských aplikacích a ne v služeb.

Svcutil.exe lze generovat nezbytné kód serializace C# z zkompilovaná sestavení pro aplikaci, proto zlepšení výkonu spouštění pro tyto aplikace. Další informace najdete v tématu [jak: Vylepšení spuštění čas z klientských aplikací WCF pomocí třídy XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

> [!NOTE]
> Svcutil.exe pouze generuje kód pro typy používané kontrakty služeb, které jsou součástí vstupní sestavení.

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|Argument|Popis|
|--------------|-----------------|
|`assemblyPath`|Určuje cestu k sestavení, který obsahuje typy kontraktů služby. Serializace typů jsou generovány pro všechny typy Xml serializovatelný v každé kontraktu.|

|Možnost|Popis|
|------------|-----------------|
|/ reference:\<cesta k souboru >|Přidá zadané sestavení na sadu sestavení, které používá k vyřešení odkazů na typy.<br /><br /> Krátký tvar: `/r`|
|/excludeType:\<typ >|Určuje plně kvalifikovaný nebo sestavením kvalifikovaný název typu, které se mají vyloučit z ověření nebo export.<br /><br /> Krátký tvar: `/et`|
|/ out:\<souboru >|Určuje název souboru pro vygenerovaný kód. Tato možnost se ignoruje, pokud více sestavení jsou předány jako vstup do nástroje.<br /><br /> Výchozí hodnota: Odvozený od názvu sestavení.<br /><br /> Krátký tvar: `/o`|
|/ UseSerializerForFaults|Určuje, že <xref:System.Xml.Serialization.XmlSerializer> by měl sloužit pro čtení a zápis chyb, místo výchozího <xref:System.Runtime.Serialization.DataContractSerializer>.|

## <a name="examples"></a>Příklady

Následující příkaz vygeneruje kód klienta ze spuštěné služby nebo online dokumentů metadat.

`svcutil http://service/metadataEndpoint`

Následující příkaz vygeneruje kód klienta z místních dokumentů metadat.

`svcutil *.wsdl *.xsd /language:C#`

Následující příkaz generuje typy kontraktů dat v jazyce Visual Basic z místních schématu dokumentů.

`svcutil /dconly *.xsd /language:VB`

Následující příkaz soubory ke stažení dokumentů metadat od spuštění služby.

`svcutil /t:metadata http://service/metadataEndpoint`

Následující příkaz generuje dokumentů metadat pro servisní smlouvy a přidružené typy v sestavení.

`svcutil myAssembly.dll`

Následující příkaz generuje dokumentů metadat služby a všechny přidružené datové typy v sestavení a kontrakty služeb.

`svcutil myServiceHost.exe /serviceName:myServiceName`

Následující příkaz generuje dokumentů metadat pro datové typy v sestavení.

`svcutil myServiceHost.exe /dconly`

Následující příkaz ověří, který je hostitelem služby.

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

Následující příkaz vygeneruje typy serializace pro <xref:System.Xml.Serialization.XmlSerializer> typů používaných modulem všechny kontrakty služeb v sestavení.

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>Kvóta pro počet znaků tabulky názvů maximální

Pokud používáte nástroj svcutil generovat metadata pro službu, může zobrazit následující zpráva:

Chyba: Nelze získat Metadata z `http://localhost:8000/somesservice/mex` při čtení dat XML se překročila kvóta pro počet znaků tabulky názvů maximální (16384). Tabulka je datová struktura používaná k uložení řetězců nalezených při zpracování XML - dlouhé dokumenty XML s neopakujícími názvy elementů, názvy atributů a hodnoty atributů mohou aktivovat tuto kvótu. Tuto kvótu jde zvýšit změnou vlastnosti MaxNameTableCharCount u objektu XmlDictionaryReaderQuotas, který se používá při vytváření čtecí funkce XML.

Tuto chybu může způsobovat služba, která vrátí velký soubor WSDL, když požádáte o jeho metadata. Problém je, že je překročena kvóta znak pro nástroje svcutil.exe. Tato hodnota nastavena, aby se zabránilo útoky na dostupnost služby (dos). Tuto kvótu můžete zvýšit tak, že zadáte následující konfigurační soubor pro svcutil.

Následující konfigurační soubor ukazuje, jak nastavit kvóty čtečky pro svcutil

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

Vytvořte nový soubor s názvem svcutil.exe.config a zkopírujte do ní ukázkový kód XML. Umístěte soubor ve stejném adresáři jako svcutil.exe. Při příštím spuštění svcutil.exe ho vyzvedne, až bude nové nastavení.

## <a name="security-concerns"></a>Zajištění zabezpečení

Odpovídající seznamu řízení přístupu (ACL) by měl používat k ochraně instalační složka nástroje Svcutil.exe pro, Svcutil.config a soubory, které neodkazují `/svcutilConfig`. To může zabránit zaregistrované a spuštění škodlivých rozšíření.

Kromě toho chcete-li minimalizovat pravděpodobnost, že dojít k ohrožení zabezpečení, neměli byste přidávat nedůvěryhodná rozšíření části systému, nebo poskytovatelé nedůvěryhodný kód pomocí Svcutil.exe.

Nakonec byste neměli používat nástroj ve střední vrstvě vaší aplikace, protože to může způsobit odepření služeb pro aktuální proces.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
