---
title: Nástroj ServiceModel Metadata Utility (Svcutil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 011f37cbbfa3eacab92705cd8e4363b36a746cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>Nástroj ServiceModel Metadata Utility (Svcutil.exe)
Nástroj ServiceModel Metadata Utility slouží ke generování kódu služby model z metadat dokumenty a dokumenty metadat z kódu modelu služby.  
  
## <a name="svcutilexe"></a>SvcUtil.exe  
 Nástroj ServiceModel Metadata Utility naleznete v umístění instalace sady Windows SDK, konkrétně C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin  
  
### <a name="functionalities"></a>Funkce  
 Následující tabulka shrnuje různé funkce poskytované tento nástroj a příslušné téma, který popisuje, jak se používají.  
  
|Úloha|Téma|  
|----------|-----------|  
|Generuje kód od spuštění služby nebo dokumenty statické metadat.|[Generování klienta WCF z metadat služby](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|  
|Exportuje dokumenty metadat z zkompilovaný kód.|[Postupy: Použití nástroje Svcutil.exe k exportu metadat z kompilovaného kódu služby](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|  
|Ověří kompilovaného kódu služby.|[Postupy: Ověření zkompilovaného kódu služby pomocí nástroje Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|  
|Soubory ke stažení dokumentů metadat od spuštění služby.|[Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|  
|Generuje kód serializace.|[Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|  
  
> [!CAUTION]
>  Svcutil přepíše stávající soubory na disku, pokud jsou identické názvy zadané jako parametry. To může zahrnovat soubory kódu, konfiguračními zásadami nebo soubory metadat. Chcete-li předejít při generování kódu a konfigurace čarou, použijte `/mergeConfig` přepínače.  
>   
>  Kromě toho `/r` a `/ct` přepínačů pro odkazování na typy jsou určeny pro vygenerování kontrakty dat. Tyto přepínače nefungují při používání třídy XmlSerializer.  
  
### <a name="timeout"></a>Časový limit  
 Nástroj má časový limit 5 minut při načítání metadat.  Tento časový limit se vztahuje pouze k načítání metadat přes síť. Nevztahuje se na žádné zpracování této metadat.  
  
### <a name="multi-targetting"></a>Více-které se budou zaměřovat  
 Nástroj nepodporuje cílení na více. Pokud chcete generovat artefaktů .NET 4 z svcutil.exe, budete muset použít svcutil.exe ze sady SDK rozhraní .NET 4. Chcete-li vygenerovat artefaktů rozhraní .NET 3.5, použijte spustitelný soubor ze sady SDK rozhraní .NET 3.5.  
  
### <a name="accessing-wsdl-documents"></a>Přístup k dokumentům WSDL  
 Pokud používáte Svcutil přístup WSDL dokument, který obsahuje odkaz na službu tokenů zabezpečení (STS), díky Svcutil WS-MetadataExchange, volání na službu STS. Služba však můžete vystavit jeho WSDL dokumentů pomocí protokolu WS-MetadataExchange nebo HTTP GET. Proto pokud služba tokenů zabezpečení je dostupná jenom v případě souboru WSDL pomocí HTTP GET klienta napsané v [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] se nezdaří. Pro klienty, které jsou napsané v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], Svcutil se pokusí použít obě WS-MetadataExchange, a k získání schématu WSDL služby tokenů zabezpečení metody GET protokolu HTTP.  
  
## <a name="using-svcutilexe"></a>Pomocí SvcUtil.exe  
  
### <a name="common-usages"></a>Běžné použití  
 Následující tabulka uvádí, že některé nejčastěji používaných možností pro tento nástroj.  
  
|Možnost|Popis|  
|------------|-----------------|  
|/ directory:\<adresáře >|Adresář pro vytvoření souborů v.<br /><br /> Výchozí hodnota: Aktuální adresář.<br /><br /> Krátkých úseků: `/d`|  
|/help|Zobrazí syntaxi příkazu a možnosti nástroje.<br /><br /> Krátkých úseků: `/?`|  
|/ nologo|Potlačení zprávy o autorských právech a hlavičku.|  
|/svcutilConfig:\<configFile>|Určuje soubor vlastní konfigurace pro použití místo souboru App.config. To slouží k registraci system.serviceModel rozšíření beze změny konfiguračního souboru nástroje.|  
|/ target:\<výstupní typ >|Určuje výstup má být vygenerován nástrojem.<br /><br /> Platné hodnoty jsou kódu, metadata nebo xmlSerializer.<br /><br /> Krátkých úseků: `/t`|  
  
### <a name="code-generation"></a>Vytvoření kódu  
 Svcutil.exe mohou generovat kód pro typy kontraktů, klientů a dat služby z dokumentů metadat. Tyto dokumenty metadat může být na odolná úložiště, nebo získat online. Načítání online následuje protokol WS-Metadata Exchange nebo protokol DISCO (podrobné informace najdete v části Stažení metadat).  
  
 Nástroje SvcUtil.exe slouží ke generování kontraktů služby a data na základě předdefinovaných dokumentu WSDL. Použijte přepínač /serviceContract a zadejte adresu URL nebo soubor umístění, kde můžete stáhnout nebo najít souboru WSDL. Tím se vygeneruje služby a data smluv, které jsou definované v dokumentu WSDL, který lze potom použít k implementaci služby předpisy. Další informace najdete v tématu [postupy: načtení metadat a implementujte kompatibilní služby](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md).  
  
 Služby s koncovým bodem vazba BasicHttpContextbinding Svcutil.exe generuje BasicHttpBinding s `allowCookies` atribut nastaven na `true` místo. Soubory cookie se používají pro kontext na serveru. Pokud chcete spravovat kontext na straně klienta, pokud služba používá soubory cookie, můžete ručně upravit konfiguraci pomocí kontextu vazby.  
  
> [!CAUTION]
>  Svcutil.exe generuje klienta na základě souboru WSDL nebo zásady přijal od služby. Hlavní název uživatele (UPN) je generována zřetězením uživatelské jméno, "\@" a plně kvalifikovaný název domény (FQDN). Pro uživatele, kteří si zaregistrovali na službě Active Directory, ale tento formát není platný a UPN generovaný nástrojem způsobí selhání v ověřování protokolem Kerberos s chybovou zprávou "Pokus o přihlášení se nezdařilo". Chcete-li vyřešit tento problém, neopravíte ručně soubor klienta generované tímto nástrojem.  
  
 `svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`  
  
|Argument|Popis|  
|--------------|-----------------|  
|`epr`|Cesta k souboru XML, který obsahuje WS-Addressing EndpointReference pro koncový bod služby, který podporuje WS-Metadata Exchange. Další informace najdete v části Stažení metadat.|  
|`metadataDocumentPath`|Cesta k dokumentu metadat (wsdl nebo xsd), který obsahuje kontrakt importovat do kódu (WSDL, XSD, .wspolicy nebo .wsmex).<br /><br /> Svcutil postupuje podle importy a zahrnuje při zadání vzdálené adresy URL pro metadata. Ale pokud chcete ke zpracování souborů metadat v místním systému souborů, musíte zadat všechny soubory v tomto argumentu. Tímto způsobem můžete použít nástroj Svcutil v prostředí sestavení kde nemůže mít závislosti sítě. Můžete použít zástupné znaky (*.xsd, \*WSDL) pro tento argument.|  
|`url`|Adresa URL pro koncový bod služby, který poskytuje metadata nebo k dokumentu metadat hostované online. Další informace o tom, jak jsou načítány tyto dokumenty najdete v části Stažení metadat.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|/Async|Generuje i synchronní a asynchronní metoda podpisy.<br /><br /> Výchozí hodnota: generování pouze synchronní metoda podpisů.<br /><br /> Krátkých úseků: `/a`|  
|/collectionType:\<typ >|Určuje typ kolekce seznamu pro klienta WCF.<br/><br /> Výchozí hodnota: typ kolekce je System.Array. <br /><br /> Krátkých úseků: `/ct`|  
|/ config:\<configFile >|Určuje název souboru pro generovaný konfiguračního souboru.<br /><br /> Výchozí: output.config|  
|/dataContractOnly|Generuje kód pro datové typy kontrakt. Nejsou generované typy kontrakt služby.<br /><br /> Měli byste zadat pouze soubory místních metadat pro tuto možnost.<br /><br /> Krátkých úseků: `/dconly`|  
|/enableDataBinding|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní na všech typech kontrakt dat povolit datové vazby.<br /><br /> Krátkých úseků: `/edb`|  
|/excludeType:\<typ >|Určuje název plně kvalifikovaný nebo sestavení kvalifikovaný typ mají být vyloučeny z typů odkazované kontrakt.<br /><br /> Při použití tohoto přepínače společně s `/r` ze samostatné knihovny DLL, celý název třídu XSD odkazuje.<br /><br /> Krátkých úseků: `/et`|  
|/importXmlTypes|Nakonfiguruje serializátor kontraktu dat k importu dat kontrakt typy jako typy IXmlSerializable.|  
|/ vnitřní|Generuje třídy, které jsou označené jako vnitřní. Výchozí hodnota: generování pouze veřejné třídy.<br /><br /> Krátkých úseků: `/i`|  
|/Language:\<jazyka >|Určuje programovací jazyk, který chcete použít pro generování kódu. Měl by poskytnout název jazyka, zaregistrovat v souboru Machine.config nebo plně kvalifikovaný název třídy, která dědí z <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Hodnoty: c#, cs, csharp, vb, visualbasic, c ++, cpp<br /><br /> Výchozí: csharp<br /><br /> Krátký tvar: `/l` **Poznámka:** přepínač podporuje pouze C++ pro zprostředkovatele kódu, který se dodává s Visual Studio 2005 SP1.|  
|/mergeConfig|Vygenerovaný konfigurace sloučí existující soubor, místo přepsal existující soubor.|  
|/messageContract|Generuje typy kontrakt zprávy.<br /><br /> Krátkých úseků: `/mc`|  
|/ NAMESPACE:\<řetězec, řetězec >|Určuje mapování z WSDL nebo schématu XML cílový obor názvů do oboru názvů CLR. Pomocí '\*' pro všechny targetNamespaces bez explicitního mapování cílový obor názvů se mapuje na tento obor názvů CLR.<br /><br /> Abyste měli jistotu, název kontraktu zpráv nejsou v konfliktu s názvem operaci, musí buď kvalifikaci odkaz na typ s `::`, nebo zkontrolujte, zda jsou jedinečné názvy.<br /><br /> Výchozí hodnota: Odvozená od cílový obor názvů dokument schématu pro kontrakty dat. Výchozí obor názvů se používá pro všechny ostatní typy vygenerovaný.<br /><br /> Krátkých úseků: `/n` **Poznámka:** při generování typy pro použití s XmlSerializer, je podporován pouze jeden obor názvů mapování. Všechny typy generovaného bude buď v výchozí obor názvů nebo obor názvů zadaný ve ' *'.|  
|/ noconfig|Nevydávají konfigurační soubory.|  
|/ nostdlib|Neodkazují na standardní knihovny.<br /><br /> Výchozí hodnota: Mscorlib.dll a System.servicemodel.dll odkazují.|  
|/ out:\<souboru >|Určuje název souboru pro generovaný kód.<br /><br /> Výchozí hodnota: Odvozené od názvu definice WSDL, WSDL název služby nebo cílí na obor názvů jednomu z schémat.<br /><br /> Krátkých úseků: `/o`|  
|/ reference:\<cesta k souboru >|Typy odkazů v zadaném sestavení. Generování klienty, když pomocí této možnosti zadejte sestavení, která může obsahovat typy, které představují metadata importována.<br /><br /> Nelze zadat kontrakty zpráv a <xref:System.Xml.Serialization.XmlSerializer> typy pomocí tohoto přepínače.<br /><br /> Pokud <xref:System.DateTimeOffset> odkazováno, tento typ se používá namísto generování nového typu. Pokud je aplikace napsaná pomocí [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], SvcUtil.exe odkazy <xref:System.DateTimeOffset> automaticky.<br /><br /> Krátkých úseků: `/r`|  
|/ serializovatelný|Generuje s atributem serializovatelné třídy.<br /><br /> Krátkých úseků: `/s`|  
|/serviceContract|Generovat kód pro pouze kontraktů služby. Třída klienta a konfigurace se nevygeneruje<br /><br /> Krátkých úseků: `/sc`|  
|/serializer:Auto|Je možné automaticky vyberte serializátor. To pokusí použít serializátor kontraktu dat a používá třídy XmlSerializer, pokud se nezdaří.<br /><br /> Krátkých úseků: `/ser`|  
|/serializer:dataContractSerializer|Generuje datové typy, které používají serializátor kontraktu dat k serializaci a deserializaci.<br /><br /> Krátkých úseků: `/ser:DataContractSerializer`|  
|/serializer:XmlSerializer|Generuje datové typy, které používají <xref:System.Xml.Serialization.XmlSerializer> k serializaci a deserializaci.<br /><br /> Krátkých úseků: `/ser:XmlSerializer`|  
|/targetClientVersion|Určit používanou verzi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] cílení aplikace. Platné hodnoty jsou `Version30` a `Version35`. Výchozí hodnota je `Version30`.<br /><br /> Krátkých úseků: `/tcv`<br /><br /> `Version30`: Použijte `/tcv:Version30` Pokud jsou generování kódu pro klienty, kteří používají [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)].<br /><br /> `Version35`: Použijte `/tcv:Version35` Pokud jsou generování kódu pro klienty, kteří používají [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Při použití `/tcv:Version35` s `/async` přepnout, i na základě událostí a jsou generovány založené nebo zpětného volání asynchronních metod. Kromě toho podporu pro LINQ povolené datové sady a <xref:System.DateTimeOffset> je povoleno.|  
|/ zabalené|Určuje, zda zvláštní případy se používá pro literál dokumentu ve dokumenty s zabalené parametry. Použití **/ zabalené** přepínač s [Service Model Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj pro určení normální velká a malá písmena.|  
  
> [!NOTE]
>  Když vazby služby je jedním z vazby poskytované systémem (najdete v části [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md)) a <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost je nastaven na hodnotu `None` nebo `Sign`, Svcutil generuje konfiguračním souboru pomocí [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element místo očekávaného elementu poskytované systémem. Například, pokud služba používá `<wsHttpBinding>` element s `ProtectionLevel` nastavena na `Sign`, vygenerované konfigurace obsahuje `<customBinding>` v části vazby místo `<wsHttpBinding>`. Další informace o úroveň ochrany, najdete v části [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md).  
  
### <a name="metadata-export"></a>Export metadat  
 Svcutil.exe můžete exportovat metadata pro služby, smlouvy a datových typů v sestaveních kompilované. Pro export metadat pro službu, je nutné použít `/serviceName` možnost zadejte službu, kterou chcete exportovat. Pokud chcete exportovat všechny typy kontraktů dat v rámci sestavení, měli byste použít `/dataContractOnly` možnost. Ve výchozím nastavení se exportují metadata pro všechny smlouvy v vstupní sestavení.  
  
 `svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`  
  
|Argument|Popis|  
|--------------|-----------------|  
|`assemblyPath`|Určuje cestu k sestavení, který obsahuje typy kontraktů služby, smluv nebo data export. Zástupné znaky standardní příkazového řádku lze zadat více souborů jako vstup.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|/serviceName:\<serviceConfigName>|Určuje název konfigurace služby pro export. Pokud tato možnost se používá, musí být předán spustitelný soubor sestavení s přidružené konfigurační soubor jako vstup. Svcutil.exe vyhledá všechny přidružené konfigurační soubory pro konfiguraci služby. Pokud konfigurační soubory, které neobsahují žádné typy rozšíření, sestavení, které obsahují tyto typy musí být v mezipaměti GAC nebo explicitně nezadá pomocí `/reference` možnost.|  
|/ reference:\<cesta k souboru >|Přidá zadané sestavení sadu sestavení, které používá pro vyřešení typu odkazy. Pokud exportujete nebo ověřování službu, která používá rozšíření 3. stran (chování, vazby a třídy BindingElements) zaregistrovaný v konfiguraci, tato možnost slouží k vyhledání sestavení rozšíření, které nejsou v mezipaměti GAC.<br /><br /> Krátkých úseků: `/r`|  
|/dataContractOnly|Pracuje s daty jenom pro typy kontrakt. Kontrakty služeb nejsou předmětem zpracování.<br /><br /> Měli byste zadat pouze soubory místních metadat pro tuto možnost.<br /><br /> Krátkých úseků: `/dconly`|  
|/excludeType:\<typ >|Určuje plně kvalifikovaný nebo sestavení kvalifikovaný název typu, které se mají vyloučit z exportu. Tuto možnost můžete použít, pokud Export metadat pro službu nebo sadu služby smluvně vyloučit typy z která je exportována. Tuto možnost nelze použít společně s `/dconly` možnost.<br /><br /> Pokud máte jednoho sestavení obsahující více služeb, a každá používá samostatné třídy se stejným názvem XSD, musíte zadat název služby místo názvu třídu XSD pro tento přepínač.<br /><br /> Kontrakt typy XSD nebo data nejsou podporovány.<br /><br /> Krátkých úseků: `/et`|  
  
### <a name="service-validation"></a>Ověření služby  
 Ověření lze použít ke zjištění chyby v implementacích služby bez hostující službu. Je nutné použít `/serviceName` možnost označte službu, kterou chcete ověřit.  
  
 `svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`  
  
|Argument|Popis|  
|--------------|-----------------|  
|`assemblyPath`|Určuje cestu k sestavení, která obsahuje typů služeb má být ověřen. Sestavení musí mít přidružený konfigurační soubor a zadejte konfiguraci služby. Standardní zástupné znaky příkazového řádku lze zadat více sestavení.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|/ ověření|Ověří implementaci služby určeného `/serviceName` možnost. Pokud tato možnost se používá, musí být předán spustitelný soubor sestavení s přidružené konfigurační soubor jako vstup.<br /><br /> Krátkých úseků: `/v`|  
|/serviceName:\<serviceConfigName>|Určuje název konfigurace služby, který má být ověřen. Svcutil.exe vyhledá všechny přidružené konfigurační soubory všechny vstupní sestavení pro konfiguraci služby. Pokud konfigurační soubory, které neobsahují žádné typy rozšíření, sestavení, která obsahuje tyto typy musí být v mezipaměti GAC nebo explicitně nezadá pomocí `/reference` možnost.|  
|/ reference:\<cesta k souboru >|Přidá zadané sestavení sadu sestavení, které používá pro vyřešení typu odkazy. Pokud exportujete nebo ověřování službu, která používá rozšíření 3. stran (chování, vazby a třídy BindingElements) zaregistrovaný v konfiguraci, tato možnost slouží k vyhledání sestavení rozšíření, které nejsou v mezipaměti GAC.<br /><br /> Krátkých úseků: `/r`|  
|/dataContractOnly|Pracuje s daty jenom pro typy kontrakt. Kontrakty služeb nejsou předmětem zpracování.<br /><br /> Měli byste zadat pouze soubory místních metadat pro tuto možnost.<br /><br /> Krátkých úseků: `/dconly`|  
|/excludeType:\<typ >|Určuje plně kvalifikovaný nebo sestavení kvalifikovaný název typu, které se mají vyloučit z ověření.<br /><br /> Krátkých úseků: `/et`|  
  
### <a name="metadata-download"></a>Stažení metadat  
 Svcutil.exe lze stáhnout metadata z službami a uložit metadata do místních souborů. Chcete-li stáhnout metadata, musíte zadat `/t:metadata` možnost. Jinak se generuje kód klienta. Pro schémata HTTP a adresy URL HTTPS Svcutil.exe pokusí se načíst metadata pomocí protokolu WS-Metadata Exchange a DISCO. Pro všechny ostatní schémata URL používá Svcutil.exe jenom WS-Metadata Exchange.  
  
 Svcutil vydává následující požadavků na metadata současně pro načtení metadat.  
  
-   Zadaná adresa požadavku MEX (WS-přenos)  
  
-   Zadaná adresa s /mex připojí požadavek MEX  
  
-   DISCO požadavku (s použitím DiscoveryClientProtocol z ASMX) pro zadaná adresa.  
  
 Ve výchozím nastavení používá Svcutil.exe vazeb definovaných v <xref:System.ServiceModel.Description.MetadataExchangeBindings> třída aby MEX požadavky. Ke konfiguraci vazby používá pro WS-Metadata Exchange, je nutné definovat koncový bod klienta v konfiguraci, která používá kontrakt IMetadataExchange. To lze definovat v konfiguračním souboru nástroje Svcutil.exe nebo v jiném souboru konfigurace zadán pomocí `/svcutilConfig` možnost.  
  
 `svcutil.exe /t:metadata  <url>* | <epr>`  
  
|Argument|Popis|  
|--------------|-----------------|  
|`url`|Adresa URL pro koncový bod služby, který poskytuje metadata nebo k dokumentu metadat hostované online.|  
|`epr`|Cesta k souboru XML, který obsahuje WS-Addressing EndpointReference pro koncový bod služby, který podporuje WS-Metadata Exchange.|  
  
### <a name="xmlserializer-type-generation"></a>Typ třídy XmlSerializer generování  
 Služby a klientské aplikace používající typy dat, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilace kódu serializace pro tyto typy dat za běhu, což může vést k pomalé spuštění výkonu.  
  
> [!NOTE]
>  Předem vygenerovaná serializace kódu je možné pouze v klientských aplikacích a není v služby.  
  
 Svcutil.exe mohou generovat nezbytné kód serializace C# z kompilované sestavení pro aplikaci, tedy zvýšení výkonu spuštění pro tyto aplikace. Další informace najdete v tématu [postupy: zlepšení spuštění čas klientských aplikací WCF pomocí třídy XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
> [!NOTE]
>  Svcutil.exe pouze generuje kód pro typy používané kontraktů služby najít ve vstupní sestavení.  
  
 `svcutil.exe /t:xmlSerializer  <assemblyPath>*`  
  
|Argument|Popis|  
|--------------|-----------------|  
|`assemblyPath`|Určuje cestu k sestavení, který obsahuje typy kontraktů služby. Typy serializace jsou generovány pro všechny Xml Serializovatelné typy v každé smlouvě.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|/ reference:\<cesta k souboru >|Přidá zadané sestavení sadu sestavení, které používá pro vyřešení typu odkazy.<br /><br /> Krátkých úseků: `/r`|  
|/excludeType:\<typ >|Určuje plně kvalifikovaný nebo sestavení kvalifikovaný název typu, které se mají vyloučit z ověření nebo export.<br /><br /> Krátkých úseků: `/et`|  
|/ out:\<souboru >|Určuje název souboru pro generovaný kód. Tato možnost je ignorována, pokud více sestavení jsou předány jako vstup pro nástroj.<br /><br /> Výchozí hodnota: Odvozená od název sestavení.<br /><br /> Krátkých úseků: `/o`|  
|/ UseSerializerForFaults|Určuje, že <!--zz <xref:System.Xml.XmlSerializer> --> `xref:System.Xml.XmlSerializer ` slouží pro čtení a zápis chyb, místo výchozího <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="examples"></a>Příklady  
 Následující příkaz generuje kód klienta z spuštěné služby nebo dokumenty online metadat.  
  
 `svcutil http://service/metadataEndpoint`  
  
 Následující příkaz generuje kód klienta z místních metadat dokumentů.  
  
 `svcutil *.wsdl *.xsd /language:C#`  
  
 Následující příkaz vytvoří typy kontraktů dat v jazyce Visual Basic z místní schéma dokumentů.  
  
 `svcutil /dconly *.xsd /language:VB`  
  
 Následující příkaz soubory ke stažení dokumentů metadat od spuštění služby.  
  
 `svcutil /t:metadata http://service/metadataEndpoint`  
  
 Následující příkaz generuje dokumenty metadat pro kontraktů služby a přidružené typy v sestavení.  
  
 `svcutil myAssembly.dll`  
  
 Následující příkaz vytvoří dokumenty metadat pro službu a všechny související kontraktů služby a datové typy v sestavení.  
  
 `svcutil myServiceHost.exe /serviceName:myServiceName`  
  
 Následující příkaz generuje dokumenty metadat pro datové typy v sestavení.  
  
 `svcutil myServiceHost.exe /dconly`  
  
 Následující příkaz ověřuje hostování služeb.  
  
 `svcutil /validate /serviceName:myServiceName myServiceHost.exe`  
  
 Následující příkaz vytvoří typy serializace pro <xref:System.Xml.Serialization.XmlSerializer> typy používané žádné kontraktů služby v sestavení.  
  
 `svcutil /t:xmlserializer myContractLibrary.exe`  
  
## <a name="maximum-nametable-character-count-quota"></a>Kvóta tabulky názvů maximální počet znaků  
 Při generování metadat pro službu pomocí svcutil, může se zobrazit následující zpráva:  
  
 Chyba: Nelze získat Metadata z http://localhost:8000/somesservice/mex při načítání dat XML byla překročena maximální tabulky názvů kvóty počtu znaků (16384). Pracovat s tabulkou názvů je datová struktura, používá k ukládání řetězců došlo během zpracování kódu XML - tuto kvótu mohou spustit dlouhé dokumentů XML bez opakování názvy elementů, atribut názvy a hodnoty atributů. Tuto kvótu zvýšit změnou MaxNameTableCharCount u objektu XmlDictionaryReaderQuotas, který používá při vytváření čtecí modul XML.  
  
 Tato chyba může být způsobeno služby, která vrací velký soubor WSDL při žádosti o jeho metadata. Problém je, že je překročena kvóta znak pro nástroje svcutil.exe. Tato hodnota nastavena na pomáhá zabránit útokům služby (dos). Tato kvóta můžete zvýšit tak, že zadáte následující konfigurační soubor pro svcutil.  
  
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
  
 Vytvořte nový soubor s názvem svcutil.exe.config a zkopírujte do ní ukázkový kód XML. Potom umístěte soubor ve stejném adresáři jako svcutil.exe. Při příštím spuštění svcutil.exe ho vyzvedne, až bude nová nastavení.  
  
## <a name="security-concerns"></a>Aspekty zabezpečení  
 Měli byste použít příslušné seznamu řízení přístupu (ACL) pro ochranu Svcutil.exe pro instalační složku, Svcutil.config a soubory, na kterou odkazoval na `/svcutilConfig`. To může zabránit škodlivých rozšíření z je zaregistrován a spustit.  
  
 Kromě toho minimalizovat riziko, že dojít k ohrožení zabezpečení, byste neměli přidat nedůvěryhodné rozšíření jako součást systému, ani používat nedůvěryhodnými zprostředkovatele s Svcutil.exe.  
  
 Nakonec byste neměli používat nástroj ve střední vrstvě vaší aplikace, neboť může to způsobit odepření služby na aktuální proces.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Postupy: Vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
