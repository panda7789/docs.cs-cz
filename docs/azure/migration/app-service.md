---
title: Migrace webové aplikace nebo služby .NET do Azure App Service
description: Přečtěte si o migraci webové aplikace nebo služby .NET z místního prostředí do Azure App Service.
ms.topic: conceptual
ms.date: 08/11/2018
ms.openlocfilehash: 57f3b981a1d94c2193160f55f9c8242da694c169
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072135"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>Migrace webové aplikace nebo služby .NET do Azure App Service

[App Service](https://docs.microsoft.com/azure/app-service/overview) je plně spravovaná služba výpočetní platformy, která je optimalizovaná pro hostování škálovatelných webů a webových aplikací. Tento článek poskytuje informace o tom, jak přenést existující aplikaci do Azure App Service, úpravy, které je potřeba vzít v úvahu, a další materiály pro [Přesun do cloudu](https://azure.microsoft.com/migration/web-applications/). Většina webů ASP.NET (WebForms, MVC) a služby (webové rozhraní API, WCF) se může přesunout přímo na Azure App Service bez jakýchkoli změn. Některé můžou potřebovat menší změny, zatímco jiné můžou potřebovat nějaký refaktoring.

Chcete začít? [Publikujte aplikaci ASP.NET + SQL pro Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).

## <a name="considerations"></a>Požadavky

### <a name="on-premises-resources-including-sql-server"></a>Místní prostředky (včetně SQL Server)

Ověřte přístup k místním prostředkům, protože může být potřeba je migrovat nebo změnit. Níže jsou uvedené možnosti pro zmírnění přístupu k místním prostředkům:

* Vytvořte síť VPN připojující App Service k místním prostředkům pomocí [Azure Virtual Networks](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet).
* Bezpečně zveřejňujte místní služby v cloudu bez změny brány firewall pomocí [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).
* Migrujte závislosti, jako je třeba [databáze SQL](https://go.microsoft.com/fwlink/?linkid=863217) do Azure.
* Využijte nabídky platforem jako služby v cloudu, abyste snížili závislosti. Například místo připojení k místnímu poštovnímu serveru zvažte použití [SendGrid](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email).

### <a name="port-bindings"></a>Vazby portů

Azure App Service podporuje port 80 pro protokol HTTP a port 443 pro přenos HTTPS.

Pro WCF jsou podporovány následující vazby:

Vazba | Poznámky
--------|--------
BasicHttp |
WSHttp |
WSDualHttpBinding | Musí být povolená [Podpora webového soketu](https://docs.microsoft.com/azure/app-service/web-sites-configure) .
NetHttpBinding | [Podpora webového soketu](https://docs.microsoft.com/azure/app-service/web-sites-configure) musí být povolena pro duplexní kontrakty.
NetHttpsBinding | [Podpora webového soketu](https://docs.microsoft.com/azure/app-service/web-sites-configure) musí být povolena pro duplexní kontrakty.
Třída BasicHttpContextBinding |
WebHttpBinding |
WSHttpContextBinding |

### <a name="authentication"></a>Authentication

Azure App Service podporuje anonymní ověřování ve výchozím nastavení a ověřování pomocí formulářů, pokud je to určeno. Ověřování systému Windows se dá použít integrací jenom s Azure Active Directory a ADFS. [Přečtěte si další informace o integraci místních adresářů s Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>Sestavení v globální mezipaměti sestavení (GAC)

Toto není podporováno. Zvažte možnost zkopírovat požadovaná sestavení do složky *\Bin* aplikace. Vlastní soubory *. msi* nainstalované na serveru (například generátory PDF) nelze použít.

### <a name="iis-settings"></a>Nastavení služby IIS
Vše, co je tradičně nakonfigurované prostřednictvím souboru applicationHost. config ve vaší aplikaci, se teď dá nakonfigurovat prostřednictvím Azure Portal. To platí pro fond bitová verze, povolení nebo zakázání WebSockets, spravované verze kanálu, verze .NET Framework (2.0/4.0) atd. Pokud chcete změnit [nastavení aplikace](https://docs.microsoft.com/azure/app-service/web-sites-configure), přejděte do [Azure Portal](https://portal.azure.com), otevřete okno pro vaši webovou aplikaci a pak vyberte kartu **nastavení aplikace** .

#### <a name="iis5-compatibility-mode"></a>Režim kompatibility IIS5
Režim kompatibility IIS5 není podporován. V Azure App Service Každá webová aplikace a všechny její aplikace běží ve stejném pracovním procesu s konkrétní sadou [fondů aplikací](https://technet.microsoft.com/library/cc735247(v=WS.10).aspx).

#### <a name="iis7-schema-compliance"></a>IIS7 + dodržování předpisů schématu  
Některé elementy a atributy nejsou definované ve Azure App Servicem schématu IIS. Pokud narazíte na problémy, zvažte použití [transformací XDT](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/).

#### <a name="single-application-pool-per-site"></a>Jeden fond aplikací na jeden web  
V Azure App Service Každá webová aplikace a všechny aplikace, které jsou v ní spuštěné, běží ve stejném fondu aplikací. Zvažte vytvoření jednoho fondu aplikací se společným nastavením nebo vytvoření samostatné webové aplikace pro každou aplikaci.

### <a name="com-and-com-components"></a>Komponenty COM a COM+  
Azure App Service nepovoluje registraci komponent modelu COM na platformě. Pokud vaše aplikace využívá jakékoli komponenty modelu COM, musí být přepsány ve spravovaném kódu a nasazeny s webem nebo aplikací.

### <a name="physical-directories"></a>Fyzické adresáře
Azure App Service nepovoluje přístup k fyzickým diskům. Pro přístup k souborům přes SMB možná budete muset použít [soubory Azure](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) . [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) může ukládat soubory pro přístup prostřednictvím protokolu HTTPS.

### <a name="isapi-filters"></a>Filtry ISAPI  
Azure App Service může podporovat použití filtrů ISAPI, ale knihovna DLL ISAPI musí být nasazena s vaší lokalitou a zaregistrována prostřednictvím souboru Web. config.

### <a name="https-bindings-and-ssl"></a>Vazby HTTPS a SSL
Vazby protokolu HTTPS nejsou migrovány, ani certifikáty SSL přidružené k vašim webům. [Certifikáty SSL je možné](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl) po dokončení migrace lokality ručně odeslat.

### <a name="sharepoint-and-frontpage"></a>SharePoint a FrontPage
SharePoint a rozšíření FrontPage Server Extensions (FPSE) nejsou podporovány.

### <a name="web-site-size"></a>Velikost webu  
Bezplatné weby mají omezení velikosti 1 GB obsahu. Pokud je váš web větší než 1 GB, musíte upgradovat na placené SKU. Viz [ceny App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="database-size"></a>Velikost databáze  
U SQL Server databází Zkontrolujte prosím aktuální [SQL Database ceny](https://azure.microsoft.com/pricing/details/sql-database).

### <a name="azure-active-directory-aad-integration"></a>Azure Active Directory (AAD) – integrace  
AAD nefunguje s bezplatnými aplikacemi. Pokud chcete používat AAD, musíte upgradovat SKU aplikace. Viz [ceny App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="monitoring-and-diagnostics"></a>Monitorování a diagnostika
Vaše aktuální místní řešení pro monitorování a diagnostiku nejsou pravděpodobně v cloudu fungovat. Azure ale poskytuje nástroje pro protokolování, monitorování a diagnostiku, abyste mohli identifikovat a ladit problémy s webovými aplikacemi. V konfiguraci můžete snadno povolit diagnostiku pro svou webovou aplikaci a můžete si zobrazit protokoly zaznamenané v Azure Application Insights. [Přečtěte si další informace o povolení protokolování diagnostiky pro webové aplikace](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>Připojovací řetězce a nastavení aplikace
Zvažte použití služby [Azure webtrezor](https://docs.microsoft.com/azure/key-vault/), která bezpečně ukládá citlivé informace používané ve vaší aplikaci. Tato data můžete také uložit jako nastavení App Service.

### <a name="dns"></a>DNS
V závislosti na požadavcích vaší aplikace možná budete muset aktualizovat konfigurace služby DNS. Tato nastavení DNS se dají nakonfigurovat v nastavení App Service [vlastní domény](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain).

## <a name="azure-app-service-with-windows-containers"></a>Azure App Service s kontejnery Windows
Pokud vaše aplikace nemůže být migrována přímo na App Service, zvažte App Service použití kontejnerů Windows, což umožňuje použití globální mezipaměti sestavení (GAC), komponent modelu COM, MSIs, úplného přístupu k rozhraním API .NET FX, rozhraní DirectX a dalším možnostem.

## <a name="see-also"></a>Viz také

* [Jak zjistit, jestli má aplikace nárok na App Service](https://appmigration.microsoft.com/)
* [Přesun databáze do cloudu](https://go.microsoft.com/fwlink/?linkid=863217)
* [Podrobnosti a omezení izolovaného prostoru webové aplikace Azure](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
