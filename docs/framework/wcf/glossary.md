---
title: "Glosář služby Windows Communication Foundation pro .NET Framework 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], glossary
- WCF [WCF], glossary
ms.assetid: 39cd36f4-8a28-4d0b-a830-98d55c9d30ae
caps.latest.revision: "243"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76cc8f456701d65b675ce7b89436da5213ea9430
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-glossary-for-net-framework-45"></a>Glosář služby Windows Communication Foundation pro .NET Framework 4.5
Následující termíny jsou definovány pro dokumentaci k Windows Communication Foundation.  
  
## <a name="terms"></a>Podmínky  
  
|Termín|Definice|  
|----------|----------------|  
|adresa|Určuje umístění, kde jsou přijaty zprávy. Je zadán jako identifikátor URI (Uniform Resource). Části schématu identifikátoru URI názvy přenosový mechanismus, který má použít pro přístup na adresu, jako je například HTTP a TCP. Hierarchická součástí identifikátor URI obsahuje jedinečné umístění, jejichž formát je závislá na přenosový mechanismus.|  
|koncový bod aplikace|Koncový bod vystavené aplikace a který odpovídá kontraktu služby implementované aplikace.|  
|chování|Chování je komponenta, která řídí různé aspekty spuštění služby, koncový bod, určité operace nebo klienta. Chování jsou seskupené podle oboru: společné chování ovlivňuje všechny koncové body globálně, pouze související se službou aspekty ovlivnit chování služby, koncový bod chování ovlivňuje pouze vlastnosti týkající se koncový bod a úrovni operace chování ovlivňuje konkrétní operace.|  
|vazba|Definuje komunikační protokoly, které se používají ke komunikaci se službou WCF. Vytvořená sady součástí názvem prvky vazby, které zásobníku přes sebe vytvořit infrastrukturu komunikace.  V tématu koncový bod.|  
|Kanál|Konkrétní implementaci prvku vazby. Představuje konfiguraci vazby a kanál je implementace přidružené k této konfiguraci. Proto je kanál, spojené s každou prvku vazby. Kanály skládat na sebe vytvořit konkrétní implementaci vazby: zásobník kanálu.|  
|zabezpečení na základě deklarace identity|Umožňuje autorizovaný přístup k chráněným prostředkům na základě deklarací.|  
|klientské aplikace|Klientská aplikace je program, který výměny zpráv pomocí jednoho nebo víc koncových bodů. Klientská aplikace začíná vytvoření instance klienta WCF a volání metod klienta WCF. Je důležité si uvědomit, že jednu aplikaci může být klienta a služby.|  
|kódování|Umožňuje vývojáři zachovat přísnou kontrolu všech součástí služby nebo klienta, a všechna nastavení provést prostřednictvím konfigurace může být prověřovány a v případě potřeby přepsat kód. Řízení aplikace, můžete udělat buď pomocí kódování, prostřednictvím konfigurace, nebo obojí.|  
|konfigurace|Konfigurace má výhodu v podobě povolení někdo než developer (například správce sítě) můžete nastavit parametry klienta a služby po zapsání kód a bez nutnosti její kompilace. Konfigurace pouze umožňuje nastavit hodnoty, jako jsou adresy koncových bodů, ale také umožňuje další ovládání povolením můžete přidat koncové body, vazeb a chování. Řízení aplikace, můžete udělat buď přes konfigurace prostřednictvím kódování, nebo obojí.|  
|kontrakt|Kontrakt je specifikace podpory pro konkrétní typ smlouvy, které je. Kontrakt služby, například je specifikace pro skupinu operací. Ve službě WCF smlouvy mají hierarchie, která je zrcadlená v objektech popis nachází v oboru názvů System.ServiceModel.Description. Kontrakt služby je nejvíc kontraktu ve WCF. Každá operace služby ve kontraktu služby má operace kontrakt, který určuje zprávy – včetně selhání zprávy – operaci může provést výměnu, a ve směru. Každá zpráva v operaci má kontrakt zprávy, specifikace pro strukturu obálky protokolu SOAP zprávy, a každý kontrakt zprávy kontrakt dat, která určuje datové struktury obsažené v zprávy.|  
|kontrakt dat|Datové typy službu, kterou používá musí být popsané v metadatech povolit ostatním uživatelům zajistit vzájemnou funkční spolupráci se službou. Popisy typů dat se označují jako kontrakt dat a typy lze v libovolnou část zprávy, například jako parametry nebo vrací typy. Pokud služba používá pouze jednoduché typy, není nutné explicitně povoleno používat kontrakty dat.|  
|deklarativní aplikace|Aplikace, která je popsána dostatečně vytvořit za běhu bez spuštění imperativní pokyny.|  
|endpoint|Se skládá z adresy, vazby a kontraktu použitých pro komunikaci se službou WCF.|  
|Adresa koncového bodu|Umožňuje vytvořit jedinečný koncový bod adresy pro každý koncový bod služby nebo za určitých podmínek sdílet adresu napříč koncovými body.|  
|Chyba – kontrakt|Kontrakt selhání může být přidružen operace služby k označení chyb, které mohou být vrácena volajícímu. Operace může obsahovat nula nebo více chyb, které jsou s ním spojená. Tyto chyby jsou SOAP chyb, které jsou modelovat jako výjimky v programovací model. Výjimka je převést na chybu protokolu SOAP, který může odeslat klientovi.|  
|hostování|V některých procesu musí být hostované služby. Hostitel je aplikace, která řídí životnost služby. Služby můžete hostovanou na vlastním nebo spravovat existující hostitelského procesu.|  
|proces hostování|Hostitelský proces je aplikace, která je určená pro hostování služeb. Mezi ně patří Internetové informační služby (IIS), aktivační služby systému Windows (WAS) a služby systému Windows. V těchto scénářích hostované hostitele řídí životnost služby. Například pomocí služby IIS nastavením virtuální adresář, který obsahuje soubor sestavení a konfiguraci služby. Po přijetí zprávy spustí službu IIS a řídí celé jeho životnosti.|  
|Inicializace operace|Operace, která je volána jako první operace novou relaci. Inicializaci jiné operace lze volat pouze po nejméně jednu operaci Inicializace byla volána.|  
|vytváření instancí modelu|Služba má model zřizování instancí. Existují tři zřizování instancí modely: &quot;jeden,&quot; ve kterém jeden objekt CLR služeb všech klientů. &quot;za volání&quot; ve kterém se vytvoří nový objekt CLR pro zpracování jednotlivých volání klienta; a &quot;relace,&quot; v které sadu CLR objekty, vytváří, jeden pro každou samostatné relaci. Volba zřizování instancí modelu závisí na požadavky na aplikace a vzoru očekávané využití služby.|  
|– zpráva|Zpráva je samostatná jednotka data, která může obsahovat několik částí, včetně text a záhlaví.|  
|kontrakt zprávy|Kontrakt zprávy popisuje formát zprávy. Například deklaruje, zda zpráva prvky by měli přejít v záhlaví a text, jakou úroveň zabezpečení má být použita na jaké elementy zprávu, a tak dále.|  
|režim zabezpečení zpráv|Režim zabezpečení zprávy určuje, že zabezpečení poskytuje implementace jeden nebo více bezpečnostní specifikací. Každá zpráva obsahuje nezbytné mechanismů pro zabezpečení během jeho přenosu a umožňuje příjemci, chcete-li zjistit případnou manipulaci a k dešifrování zpráv. V této smysl je zabezpečení zapouzdřený v rámci každé zprávy, zajištění zabezpečení začátku do konce napříč více segmenty směrování. Protože informace o zabezpečení stane součástí zprávy, je také možné zahrnout více druhů přihlašovací údaje se zprávou (to se označují jako deklarace identity). Tento přístup také nabízí výhodu v podobě povolení zprávu, která se bezpečně procházet přes všechny přenos, včetně více přenosy mezi jeho původní a cílové. Nevýhodou tohoto přístupu je složitosti kryptografických mechanismů zaměstnání, což vede k ovlivnit výkon.|  
|metadata|Metadata služby jsou popsané charakteristiky služby, která externí entity je potřeba pochopit ke komunikaci se službou. Metadata mohou být spotřebovávána ServiceModel Metadata Utility Tool (Svcutil.exe) pro generování klienta WCF a doprovodné konfigurace, který klientská aplikace můžete použít k interakci se službou.  Metadata vystavené služba zahrnuje dokumentech schémat XML, které definují kontrakt dat služby, a WSDL dokumenty, které popisují metody služby.  Když je povolené, metadata pro službu automaticky generuje služba WCF zkontrolováním služba a její koncové body. K publikování metadat ze služby, je potřeba explicitně povolit chování metadat.|  
|operace kontraktu|Operaci kontrakt definuje parametry a návratový typ operace. Při vytváření rozhraní, které definuje kontrakt služby, souhlasíte s použitím atribut T:System.ServiceModel.OperationContractAttribute na každou definici metody, která je součástí smlouvy operaci kontrakt. Operace můžete modelován jako přepnutím do jedné zprávy a vrátilo se do jedné zprávy, nebo jako trvá sadu typů a vrácení typu. V takovém případě systém určí formát zprávy, které se vyměňují pro tuto operaci.|  
|Projekce|Reprezentace dat v drátové síti. Například SOAP projekce odešle zprávy jako obálky protokolu SOAP a projekce webové odesílá zprávy ve formátu JSON.|  
|zabezpečení|Zabezpečení ve WCF zahrnuje důvěrnost (šifrování zpráv, aby se zabránilo odposlouchávání), integritu (znamená pro zjišťování manipulaci se zprávou), ověřování (prostředky pro ověření serverů a klientů) a autorizace (řízení přístup k prostředkům). Tyto funkce jsou k dispozici buď využívání stávající mechanismy zabezpečení, jako je například TLS přes protokol HTTP (také označované jako HTTPS), nebo implementovat jednu nebo více různých WS-* bezpečnostní specifikací.|  
|služba s vlastním hostováním|Služba s vlastním hostováním je ten, který běží v rámci procesu aplikace, který vytvořili vývojáři. Vývojář celé jeho životnosti ovládací prvky, nastaví vlastnosti služby, otevře služby (která ji nastaví do režimu naslouchání) a ukončení služby.|  
|service|Program nebo proces, který vystavuje jeden nebo více koncových bodů s každý koncový bod vystavení jednu nebo více operací.|  
|kontrakt služby|Kontrakt služby sváže společně více souvisejících operací do jedné jednotky funkční. Nastavení úrovně služby, například obor názvů služby, odpovídající kontrakt zpětného volání a jiné těchto nastavení můžete definovat kontrakt. Ve většině případů je definována kontrakt vytváření rozhraní ve programovací jazyk podle vašeho výběru a použití atributu T:System.ServiceModel.ServiceContractAttribute na rozhraní. Výsledky skutečných služby kódu implementací rozhraní.|  
|operaci služby|Operace služby je procedura definované v kódu služby, která implementuje funkce pro operaci. Tato operace je pro klienty zpřístupněná jako metody pro klienta WCF. Metoda může vrátit hodnotu, může trvat libovolný počet argumentů, nebo nepřebírají žádné argumenty a vrátit žádná odpověď. Například operace, která funguje jako &quot;Hello&quot; lze použít jako oznámení o stavu klienta a zahájíte řady operací.|  
|vazby poskytované systémem|WCF zahrnuje několik vazeb poskytovaných systémem. Toto jsou kolekce elementů, které jsou optimalizované pro určité scénáře vazby. Například T:System.ServiceModel.WSHttpBinding slouží pro spolupráci s služby, které implementují různé WS-* specifikace. Tyto vazby ušetřit čas tím, že předloží pouze možnosti, které mohou být správně použity pro konkrétní scénář. Pokud jeden z těchto vazeb nesplňuje vaše požadavky, můžete vytvořit vlastní vlastní vazby.|  
|ukončení operace|Operace, která je volána jako poslední zprávy v existující relaci. V případě výchozí WCF recykluje objektu služby a jeho kontextu po uzavření relace, ke kterému se vztahovaly službu.|  
|režim zabezpečení přenosu|Zabezpečení lze zadat pomocí jedné z tři režimy: přenosu režim, režim zabezpečení zprávy a přenos s režim zprávy přihlašovacích údajů. Režim zabezpečení přenosu Určuje, že důvěrnost, integritu a ověřování jsou poskytovány na mechanismy transport layer (jako je například HTTPS). Při použití přenosu jako protokol HTTPS, tento režim má výhodu v podobě se efektivní v jeho výkon a popsaných z důvodu jeho jejich rozšíření na Internetu. Nevýhodou je, že je tento druh zabezpečení samostatně použitá jednotlivých směrování v cestě komunikace, což komunikace náchylné k &quot;prostředníka&quot; útoku.|  
|přenos s režim zabezpečení přihlašovacích údajů zprávy|Tento režim používá k zajištění důvěrnosti, ověřování a integritu zprávy, když všechny zprávy může obsahovat více přihlašovací údaje (deklarace identity) vyžaduje, že příjemci zprávy do přenosové vrstvy.|  
|převaděče typů|Typ CLR může být přidružen jeden nebo více System.ComponentModel.TypeConverter odvozených typů, které umožňují převodu instance typu CLR do a z instancí jiné typy. Typ converterr je spojena s typem CLR pomocí atributu System.ComponentModel.TypeConverterAttribute.  TypeConverterAttribute lze přímo na typ CLR nebo vlastnost. Převaděče typu zadaná u vlastnosti vždy má přednost před převaděč typ zadaný v typu CLR vlastnosti.|  
|Klienta WCF|Klienta WCF je konstrukce klientskou aplikaci, která zveřejňuje operací služby jako metody (v rozhraní .NET Framework programovací jazyk podle vaší volby, jako je například jazyka Visual Basic a Visual C#). Všechny aplikace, může hostovat klienta WCF, včetně aplikace, který je hostitelem služby. Proto je možné vytvořit službu, která zahrnuje klienti WCF dalších služeb.  Mohou být automaticky generovány v nástroji ServiceModel Metadata Utility (Svcutil.exe) a odkazující na spuštěnou službu, která publikuje metadat klienta WCF.|  
|Služby pracovních postupů|Služby pracovních postupů je služba WCF, která je implementovaná jako pracovní postup. Pracovní postup obsahuje zasílání zpráv aktivit, které odesílat nebo přijímat zprávy WCF.|  
|WS-*|Sdružená vlastnost rostoucí sadu webové služby (WS) specifikace, jako je WS-zabezpečení, WS-ReliableMessaging a tak dále, které jsou implementované ve WCF.|  
|XAML|eXtensible Application Markup Language|  
|Schématu XAML|Schéma kód používá k definování custome typy v jazyce XAML.|
