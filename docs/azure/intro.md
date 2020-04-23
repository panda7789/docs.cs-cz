---
title: Začínáme s Azure a .NET
description: Seznamte se se základy, které potřebujete vědět o Azure a .NET.
ms.date: 03/15/2020
ms.openlocfilehash: 64defed4433647c2a0dcce91493d9ec77d21b541
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072142"
---
# <a name="introduction-to-azure-and-net"></a>Seznámení s Azure a .NET

Tento dokument poskytuje přehled klíčových konceptů a služeb .NET vývojáři by měli být obeznámeni s začít vývoj aplikací pomocí služeb Azure.

## <a name="key-concepts"></a>Klíčové koncepty

**Účet Azure**: Váš účet Azure je přihlašovací údaje, které používáte k přihlášení ke službám Azure, jako je [Azure Portal](https://portal.azure.com) nebo [Cloud Shell](https://shell.azure.com). Pokud nemáte účet Azure, můžete [si ho vytvořit zdarma](https://azure.microsoft.com/free/dotnet/).

**Předplatné Azure**: Předplatné je fakturační plán, ve kterém se vytvářejí prostředky Azure. Předplatná mohou být jednotlivá předplatná nebo podniková předplatná spravovaná vaší společností. Váš účet Azure lze přidružit k více předplatným. V takovém případě se ujistěte, že při vytváření prostředků vybíráte správné předplatné. Další informace naleznete [v tématu Principy účtů, předplatných a fakturace](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

> [!TIP]
> Pokud máte předplatné Visual Studia, [máte měsíční kredity Azure, které čekají na aktivaci](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

**Skupina prostředků**: Skupiny prostředků jsou způsob, jak uspořádat prostředky Azure do skupin pro správu. Prostředky vytvořené v Azure se uloží do skupiny prostředků, podobně jako uložení souboru do složky v počítači.

**Hostování**: Chcete-li spustit kód v Azure, musí být hostován ve službě, která podporuje provádění kódu poskytovaného uživatelem.

**Spravované služby**: Azure poskytuje některé služby, kde poskytujete data nebo informace do Azure, a implementace Azure provede příslušnou akci. Jedním z příkladů je Azure Blob Storage, kde poskytujete soubory a Azure zpracovává čtení, zápis a jejich uchování.

## <a name="choosing-a-hosting-option"></a>Výběr možnosti hostování

Hostování v Azure lze rozdělit do tří kategorií.

* **Infrastruktura jako služba (IaaS)**: S IaaS zřídíte virtuální počítače, které potřebujete, spolu s přidruženými síťovými a úložnými součástmi. Potom nasadit jakýkoli software a aplikace, které chcete na tyto virtuální počítače. Tento model je nejblíže k tradičnímu místnímu prostředí s tím rozdílem, že Microsoft spravuje infrastrukturu. Stále spravujete jednotlivé virtuální počítače, včetně operačního systému, vlastního softwaru a aktualizací zabezpečení.

* **Platforma jako služba (PaaS):** PaaS poskytuje spravované hostitelské prostředí, ve kterém nasazujete aplikaci bez nutnosti spravovat virtuální počítače nebo síťové prostředky. Například místo vytváření jednotlivých virtuálních počítačů zadáte počet instancí a služba zřídí, nakonfiguruje a spravuje potřebné prostředky. Azure App Service je příkladem služby PaaS.
  
* **Funkce jako služba (FaaS)**: Běžně označované jako bezserverové výpočetní techniky, FaaS jde ještě dále než PaaS v abstrakce obavy hostitelského prostředí. Místo vytváření výpočetních instancí a následného nasazení kódu do těchto instancí nasadíte kód a služba jej automaticky spustí. Není nutné spravovat výpočetní prostředky. Platforma bez problémů škáluje váš kód nahoru nebo dolů na jakoukoli úroveň potřebnou ke zpracování provozu a platíte pouze v případě, že je váš kód spuštěn. Azure Functions je služba FaaS.

Obecně platí, že čím více vaše aplikace upřednostňuje modely FaaS a PaaS, tím více výhod uvidíte z běhu v cloudu. Níže je uveden přehled tří běžných možností hostování v Azure a kdy si je vybrat.

* [Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is): Pokud hledáte hostování webové aplikace nebo služby, podívejte se nejprve na App Service. Pokud chcete začít používat Službu Aplikací a ASP.NET, WCF a ASP.NET základních aplikací, přečtěte si hlavní informace [o vytvoření ASP.NET webové aplikace v Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet).

* [Funkce Azure:](https://docs.microsoft.com/azure/azure-functions/functions-overview)Funkce Azure jsou skvělé pro pracovní postupy řízené událostmi. Mezi příklady patří reakce na webhooky, zpracování položek ve frontách nebo úložiště objektů blob a časovače. Pokud chcete začít s Funkcemi Azure, [přečtěte si](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)část Vytvoření první funkce pomocí Visual Studia .

* [Virtuální počítače Azure:](https://docs.microsoft.com/azure/virtual-machines/)Pokud služba App Service nevyhovuje vašim potřebám pro hostování existující aplikace z důvodu konkrétnízávislosti, virtuální počítače bude nejjednodušší místo pro spuštění. Pokud chcete začít s virtuálními počítači a ASP.NET nebo WCF, přečtěte si informace [o nasazení ASP.NET aplikace do virtuálního počítače Azure](https://tutorials.visualstudio.com/aspnet-vm/intro).

> [!TIP]
> Další informace o výběru služby najdete v [tématu Výběr výpočetní služby Azure pro vaši aplikaci](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree).

## <a name="choose-a-data-storage-service"></a>Výběr služby pro ukládání dat

Azure nabízí několik služeb pro ukládání dat v závislosti na vašich potřebách. Nejběžnější datové služby pro vývojáře rozhraní .NET jsou:

* [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/): Pokud chcete migrovat aplikaci, která už používá SQL Server do cloudu, Azure SQL Database je přirozené místo pro spuštění. Další informace najdete [v tématu Výuka: Vytvoření aplikace ASP.NET v Azure s databází SQL](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase)Database .

* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/): Azure Cosmos DB je moderní databáze určená pro cloud. Při spuštění nové aplikace, která ještě nemá závislost na konkrétní databázi, měli byste se podívat na Azure Cosmos DB. Cosmos DB je dobrou volbou pro nové webové, mobilní, herní a IoT aplikace, kde je důležité automatické škálování, předvídatelný výkon, rychlé doby odezvy a možnost dotazovat se na data bez schématu. Další informace najdete [v tématu Úvodní příručka: Vytvoření webové aplikace .NET s Azure Cosmos DB pomocí rozhraní SQL API a portálu Azure](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).

* [Azure Blob Storage](https://docs.microsoft.com/azure/storage/): Azure Blob Storage je optimalizované pro ukládání a načítání velkých binárních objektů, jako jsou image, soubory a datové proudy. Úložiště objektů umožňují správu extrémně velkého množství nestrukturovaných dat. Začněte najdete [v tématu Úvodní příručka: Vytvoření objektu blob v úložišti objektů pomocí rozhraní .NET](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet).

> [!TIP]
> Další informace najdete v [tématu Výběr správného úložiště dat](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview).

## <a name="connect-to-azure-services"></a>Připojení ke službám Azure

Pokud používáte Visual Studio, můžete do svých projektů přidat podporu pro určité služby Azure. Dialogové **okno Připojené služby** v sadě Visual Studio poskytuje snadný způsob, jak do projektů přidat všechny požadované odkazy, kód připojení a nastavení konfigurace. Některé běžně používané služby Azure jsou podporovány ipozahovací, jako je [úložiště](/azure/vs-azure-tools-connected-services-storage), ověřování [Azure Active Directory,](/azure/active-directory/develop/vs-active-directory-add-connected-service) Trezor klíčů [Azure](/azure/key-vault/vs-key-vault-add-connected-service)a [kognitivní služby,](/azure/cognitive-services/) jako je [počítačové vidění](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service). Další služby, včetně služeb třetích stran, jsou k dispozici jako rozšíření na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance).

## <a name="diagnosing-problems-in-the-cloud"></a>Diagnostika problémů v cloudu
Jakmile nasadíte aplikaci do Azure, můžete se spouštět do případů, kdy fungovala ve vývoji, ale není v Azure. Níže jsou dvě dobrá místa, která můžete začít při diagnostice problémů:

* **Vzdálené ladění z Visual Studia:** Většina výpočetních služeb Azure (včetně služeb popsaných v tomto dokumentu) podporuje vzdálené ladění pomocí sady Visual Studio a získávání protokolů. Chcete-li prozkoumat možnosti sady Visual Studio s vaší aplikací, otevřete okno nástroje Průzkumníka cloudu zadáním "Cloud Explorer" do panelu nástrojů pro rychlé spuštění sady Visual Studio (v pravém horním rohu) a pak vyhledejte aplikaci ve stromu. Podrobnosti najdete [v tématu Poradce při potížích s webovou aplikací ve službě Azure App Service pomocí Visual Studia](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).

* **Application Insights**: [Application Insights](https://docs.microsoft.com/azure/application-insights/) je kompletní řešení pro monitorování výkonu aplikací (APM), které automaticky zachycuje diagnostická data, telemetrii a data o výkonu z aplikací. Informace o tom, jak začít shromažďovat diagnostická data pro vaši aplikaci, najdete v tématu [Zahájení sledování ASP.NET webové aplikace](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal).

## <a name="next-steps"></a>Další kroky

* [Nasazení první webové aplikace ASP.NET Core do Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)
* [Informace o ověřování v Azure SDK pro rozhraní .NET](./sdk/authentication.md)
* [Diagnostika chyb v cloudových aplikacích](https://blogs.msdn.microsoft.com/webdev/2018/02/07/diagnosing-errors-on-your-cloud-apps)
* Stáhněte si bezplatnou e-knihu [Azure Quick Start Guide pro vývojáře rozhraní .NET](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook)
