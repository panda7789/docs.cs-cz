---
title: Migrace webové aplikace nebo služby .NET do služby Azure App Service
description: Přečtěte si o migraci webové aplikace nebo služby .NET z místní do služby Azure App Service.
ms.topic: conceptual
ms.date: 08/11/2018
ms.openlocfilehash: 57f3b981a1d94c2193160f55f9c8242da694c169
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072135"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a>Migrace webové aplikace nebo služby .NET do služby Azure App Service

[App Service](https://docs.microsoft.com/azure/app-service/overview) je plně spravovaná služba výpočetní platformy, která je optimalizovaná pro hostování škálovatelných webů a webových aplikací. Tento článek obsahuje informace o tom, jak zvedat a přesouvat existující aplikaci do služby Azure App Service, úpravy, které je třeba zvážit, a další prostředky pro [přechod do cloudu](https://azure.microsoft.com/migration/web-applications/). Většina ASP.NET weby (webové stránky, MVC) a služby (webové rozhraní API, WCF) se můžou beze změn přesunout přímo do služby Azure App Service. Některé mohou potřebovat drobné změny, zatímco jiné mohou potřebovat některé refaktoring.

Chcete začít? [Publikujte svou ASP.NET + SQL aplikaci do služby Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).

## <a name="considerations"></a>Požadavky

### <a name="on-premises-resources-including-sql-server"></a>Místní prostředky (včetně SERVERU SQL)

Ověřte přístup k místním prostředkům, protože je možné, že je nutné je migrovat nebo změnit. Následují možnosti pro zmírnění přístupu k místním prostředkům:

* Vytvořte vpn spojující službu App Service s místními prostředky pomocí [virtuálních sítí Azure](https://docs.microsoft.com/azure/app-service/web-sites-integrate-with-vnet).
* Bezpečně vystavit místní služby do cloudu bez změn brány firewall pomocí [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).
* Migrujte závislosti, jako je [například databáze SQL](https://go.microsoft.com/fwlink/?linkid=863217) do Azure.
* Pomocí nabídky platformy jako služby v cloudu můžete snížit počet závislostí. Například místo připojení k místnímu poštovnímu serveru zvažte použití [sendgridu](https://docs.microsoft.com/azure/sendgrid-dotnet-how-to-send-email).

### <a name="port-bindings"></a>Vazby portů

Služba Azure App Service podporuje port 80 pro protokol HTTP a port 443 pro provoz HTTPS.

Pro WCF jsou podporovány následující vazby:

Vazba | Poznámky
--------|--------
Základní http |
WShttp |
WSDualhttpVazba | [Podpora webového soketu](https://docs.microsoft.com/azure/app-service/web-sites-configure) musí být povolena.
Síťová vazba | [Podpora webového soketu](https://docs.microsoft.com/azure/app-service/web-sites-configure) musí být povolena pro duplexní smlouvy.
Síťová vazba | [Podpora webového soketu](https://docs.microsoft.com/azure/app-service/web-sites-configure) musí být povolena pro duplexní smlouvy.
ZákladníhttpContextbinding |
Vazba na webhttp |
WShttpContextbinding |

### <a name="authentication"></a>Authentication

Služba Azure App Service podporuje ve výchozím nastavení anonymní ověřování a ověřování pomocí formulářů, pokud to je zamýšleno. Ověřování systému Windows lze použít pouze při integraci se službou Azure Active Directory a službou ADFS. [Přečtěte si další informace o integraci místních adresářů pomocí služby Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

### <a name="assemblies-in-the-gac-global-assembly-cache"></a>Sestavení v GAC (globální mezipaměť sestavení)

Toto není podporováno. Zvažte zkopírování požadovaných sestavení do složky *\bin* aplikace. Vlastní soubory *MSI* nainstalované na serveru (například generátory PDF) nelze použít.

### <a name="iis-settings"></a>Nastavení služby IIS
Vše, co se tradičně nakonfigurovalo pomocí applicationHost.config ve vaší aplikaci, teď můžete nakonfigurovat na webu Azure Portal. To platí pro bitness AppPool, povolit/zakázat WebSockets, spravované verze kanálu, .NET Framework verze (2.0/4.0) a tak dále. Chcete-li změnit [nastavení aplikace](https://docs.microsoft.com/azure/app-service/web-sites-configure), přejděte na [portál Azure](https://portal.azure.com), otevřete okno pro webovou aplikaci a vyberte kartu **Nastavení aplikace.**

#### <a name="iis5-compatibility-mode"></a>Režim kompatibility iIS5
Režim kompatibility iIS5 není podporován. Ve službě Azure App Service se každá webová aplikace a všechny aplikace pod ní spouštějí ve stejném pracovním procesu s konkrétní sadou [fondů aplikací](https://technet.microsoft.com/library/cc735247(v=WS.10).aspx).

#### <a name="iis7-schema-compliance"></a>Dodržování zásad schématu IIS7+  
Některé prvky a atributy nejsou definovány ve schématu služby Azure App Service IIS. Pokud narazíte na problémy, zvažte použití [XDT transformace](https://azure.microsoft.com/documentation/articles/web-sites-transform-extend/).

#### <a name="single-application-pool-per-site"></a>Fond jednotlivých aplikací na lokalitu  
Ve službě Azure App Service se každá webová aplikace a všechny aplikace pod ní spouštějí ve stejném fondu aplikací. Zvažte vytvoření jednoho fondu aplikací se společným nastavením nebo vytvoření samostatné webové aplikace pro každou aplikaci.

### <a name="com-and-com-components"></a>Komponenty modelu COM a COM+  
Azure App Service neumožňuje registraci komponent MODELU COM na platformě. Pokud vaše aplikace využívá nějaké součásti modelu COM, je třeba je přepsat ve spravovaném kódu a nasadit s webem nebo aplikací.

### <a name="physical-directories"></a>Fyzické adresáře
Azure App Service neumožňuje přístup k fyzické jednotce. Možná budete muset použít [soubory Azure](https://docs.microsoft.com/azure/storage/files/storage-files-introduction) pro přístup k souborům přes SMB. [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) můžete ukládat soubory pro přístup přes PROTOKOL HTTPS.

### <a name="isapi-filters"></a>Filtry ISAPI  
Služba Azure App Service může podporovat použití filtrů ISAPI, ale dll ISAPI musí být nasazena s vaším webem a registrována prostřednictvím web.config.

### <a name="https-bindings-and-ssl"></a>Vazby HTTPS a SSL
Vazby HTTPS nejsou migrovány, stejně jako certifikáty SSL přidružené k vašim webovým serverům. [Certifikáty SSL lze](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-ssl) však po dokončení migrace webu ručně odeslat.

### <a name="sharepoint-and-frontpage"></a>SharePoint a Aplikace FrontPage
Rozšíření SharePoint a FrontPage Server Extensions (FPSE) nejsou podporována.

### <a name="web-site-size"></a>Velikost webu  
Bezplatné weby mají limit velikosti 1 GB obsahu. Pokud je váš web větší než 1 GB, musíte upgradovat na placenou skladovou položku. Viz [Ceny služby App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="database-size"></a>Velikost databáze  
U databází serveru SQL Server zkontrolujte aktuální [ceny databáze SQL](https://azure.microsoft.com/pricing/details/sql-database).

### <a name="azure-active-directory-aad-integration"></a>Integrace služby Azure Active Directory (AAD)  
AAD nefunguje s bezplatnými aplikacemi. Chcete-li použít AAD, musíte upgradovat skladovou položku aplikace. Viz [Ceny služby App Service](https://azure.microsoft.com/pricing/details/app-service/windows/).

### <a name="monitoring-and-diagnostics"></a>Monitorování a diagnostika
Vaše aktuální místní řešení pro monitorování a diagnostiku pravděpodobně nebudou fungovat v cloudu. Azure však poskytuje nástroje pro protokolování, monitorování a diagnostiku, takže můžete identifikovat a ladit problémy s webovými aplikacemi. Diagnostiku webové aplikace můžete snadno povolit v její konfiguraci a můžete zobrazit protokoly zaznamenané v Azure Application Insights. [Další informace o povolení protokolování diagnostiky pro webové aplikace](https://docs.microsoft.com/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="connection-strings-and-application-settings"></a>Připojovací řetězce a nastavení aplikace
Zvažte použití [Azure KeyVault](https://docs.microsoft.com/azure/key-vault/), služba, která bezpečně ukládá citlivé informace používané ve vaší aplikaci. Případně můžete tato data uložit jako nastavení služby App Service.

### <a name="dns"></a>DNS
Možná budete muset aktualizovat konfigurace DNS na základě požadavků vaší aplikace. Tato nastavení DNS lze nakonfigurovat v [nastavení vlastní domény](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-custom-domain)služby App Service .

## <a name="azure-app-service-with-windows-containers"></a>Služba Azure App Service s kontejnery s Windows
Pokud vaši aplikaci nelze migrovat přímo do služby App Service, zvažte službu App Service pomocí kontejnerů Windows, která umožňuje použití GAC, komponent com, MSI, úplný přístup k rozhraním API .NET FX, DirectX a dalším.

## <a name="see-also"></a>Viz také

* [Jak zjistit, jestli vaše aplikace splňuje podmínky pro službu App Service](https://appmigration.microsoft.com/)
* [Přesunutí databáze do cloudu](https://go.microsoft.com/fwlink/?linkid=863217)
* [Podrobnosti a omezení izolovaného prostoru webové aplikace Azure](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
