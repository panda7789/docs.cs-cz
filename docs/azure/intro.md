---
title: Začínáme s Azure a .NET
description: Seznamte se se základy, které potřebujete vědět o Azure a .NET.
ms.date: 03/15/2020
ms.openlocfilehash: d57d1d50852c9d7fff099554bd64c48c15129bb4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446389"
---
# <a name="introduction-to-azure-and-net"></a>Seznámení s Azure a .NET

Tento dokument poskytuje přehled klíčových konceptů a služeb pro vývojáře v rozhraní .NET, které by měly být obeznámené s cílem začít vyvíjet aplikace pomocí služeb Azure.

## <a name="key-concepts"></a>Klíčové koncepty

**Účet Azure**: váš účet Azure je přihlašovací údaje, které používáte k přihlášení ke službám Azure, jako je například [Azure Portal](https://portal.azure.com) nebo [Cloud Shell](https://shell.azure.com). Pokud účet Azure nemáte, můžete si [ho vytvořit zdarma](https://azure.microsoft.com/free/dotnet/).

**Předplatné Azure**: předplatné je fakturační plán, ve kterém se vytvářejí prostředky Azure. Předplatná můžou být jednotlivá předplatná nebo podniková předplatná, která spravuje vaše společnost. Váš účet Azure je možné přidružit k několika předplatným. V takovém případě se ujistěte, že vybíráte správné předplatné při vytváření prostředků. Další informace najdete v tématu [Principy účtů, předplatných a fakturace](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).

> [!TIP]
> Pokud máte předplatné sady Visual Studio, [máte měsíční kredity Azure čekající na aktivaci](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).

**Skupina prostředků**: skupiny prostředků představují způsob, jak uspořádat prostředky Azure do skupin pro správu. Prostředky vytvořené v Azure se uloží do skupiny prostředků, podobně jako ukládání souboru do složky v počítači.

**Hostování**: Pokud chcete spustit kód v Azure, musí být hostovaný ve službě, která podporuje spouštění kódu zadaného uživatelem.

**Spravované služby**: Azure poskytuje některé služby, ve kterých zadáte data nebo informace do Azure, a implementace Azure provede příslušnou akci. Jedním z příkladů je Azure Blob Storage, kde zadáváte soubory a Azure zpracovává čtení, zápis a uchování těchto souborů.

## <a name="choosing-a-hosting-option"></a>Výběr možnosti hostování

Hostování v Azure je možné rozdělit do tří kategorií.

* **Infrastruktura jako služba (IaaS)**: v IaaS můžete zřídit virtuální počítače, které potřebujete, spolu s přidruženými součástmi sítě a úložiště. Pak na tyto virtuální počítače nasadíte jakýkoli software a aplikace, které chcete. Tento model je nejblíže tradičnímu místnímu prostředí s tím rozdílem, že společnost Microsoft spravuje infrastrukturu. Pořád budete spravovat jednotlivé virtuální počítače, včetně operačního systému, vlastního softwaru a aktualizací zabezpečení.

* **Platforma jako služba (PaaS)**: PaaS poskytuje spravované hostitelské prostředí, ve kterém nasadíte aplikaci, aniž byste museli spravovat virtuální počítače nebo síťové prostředky. Například místo vytváření jednotlivých virtuálních počítačů zadáte počet instancí a služba zřídí, nakonfiguruje a spravuje potřebné prostředky. Azure App Service je příkladem služby PaaS.
  
* **Functions as-a-Service (FaaS)**: obvykle se označuje jako výpočetní prostředí bez serveru, FaaS ještě více než PaaS při abstrakci týkající se tohoto hostitelského prostředí. Namísto vytváření výpočetních instancí a následného nasazení kódu do těchto instancí nasadíte kód a služba ho automaticky spustí. Nemusíte spravovat výpočetní prostředky. Platforma bez problémů škáluje váš kód nahoru nebo dolů na libovolnou úroveň nezbytnou pro zpracování provozu a platíte jenom v případě, že je váš kód spuštěný. Azure Functions je služba FaaS.

Obecně platí, že víc vašich aplikací přináší FaaS a PaaS modely. tím více výhod uvidíte, jak se v cloudu spouští. Níže je uveden přehled tří běžných možností hostování v Azure a jejich výběr.

* [Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is): Pokud chcete hostovat webovou aplikaci nebo službu, podívejte se nejprve na App Service. Pokud chcete začít s aplikacemi App Service a ASP.NET, WCF a ASP.NET Core, přečtěte si téma [Vytvoření webové aplikace v ASP.NET Core v Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet).

* [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview): Azure Functions je skvělé pro pracovní postupy řízené událostmi. Mezi příklady patří reakce na Webhooky, zpracování položek ve frontách nebo BLOB Storage a časovače. Chcete-li začít s Azure Functions, přečtěte si téma [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

* [Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/): Pokud App Service nevyhovuje vašim požadavkům na hostování stávající aplikace z důvodu konkrétních závislostí, Virtual Machines bude nejjednodušší místo pro spuštění. Pokud chcete začít s Virtual Machines a ASP.NET nebo WCF, přečtěte si téma [nasazení aplikace ASP.NET na virtuální počítač Azure](https://tutorials.visualstudio.com/aspnet-vm/intro).

> [!TIP]
> Další informace o výběru služby najdete v tématu [Volba služby COMPUTE Azure pro vaši aplikaci](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree).

## <a name="choose-a-data-storage-service"></a>Zvolit službu úložiště dat

Azure nabízí několik služeb pro ukládání vašich dat v závislosti na vašich potřebách. Nejběžnějšími datovými službami pro vývojáře v rozhraní .NET jsou:

* [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/): Pokud chcete migrovat aplikaci, která už používá SQL Server v cloudu, Azure SQL Database je přirozeným místem, kde začít. Informace o tom, jak začít, najdete v tématu [kurz: sestavení aplikace v ASP.NET v Azure pomocí SQL Database](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase).

* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/): Azure Cosmos DB je moderní databáze navržená pro Cloud. Když spouštíte novou aplikaci, která ještě nemá konkrétní závislost databáze, měli byste se podívat na Azure Cosmos DB. Cosmos DB je vhodná volba pro nové webové, mobilní a herní aplikace a aplikace IoT, kde jsou důležité automatické škálování, předvídatelný výkon, doba rychlé odezvy a možnost dotazování na data bez schémat. Informace o tom, jak začít, najdete v tématu [rychlý Start: Vytvoření webové aplikace .NET s Azure Cosmos DB pomocí rozhraní SQL API a Azure Portal](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).

* [Azure BLOB Storage](https://docs.microsoft.com/azure/storage/): Azure Blob Storage je optimalizovaná pro ukládání a načítání velkých binárních objektů, jako jsou obrázky, soubory a streamy. Úložiště objektů umožňují správu extrémně velkých objemů nestrukturovaných dat. Informace o tom, jak začít, najdete [v tématu rychlý Start: použití .NET k vytvoření objektu BLOB v úložišti objektů](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet).

> [!TIP]
> Další informace najdete v tématu [Volba správného úložiště dat](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview).

## <a name="connect-to-azure-services"></a>Připojení ke službám Azure

Pokud používáte Visual Studio, můžete do svých projektů přidat podporu pro určité služby Azure. Dialogové okno **připojené služby** v aplikaci Visual Studio poskytuje snadný způsob, jak přidat všechny požadované odkazy, kód připojení a nastavení konfigurace do vašich projektů. Některé běžně používané služby Azure jsou podporované mimo pole, jako je [úložiště](/azure/vs-azure-tools-connected-services-storage), [Azure Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) ověřování, [Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)a [Cognitive Services](/azure/cognitive-services/) , jako je například [počítačové zpracování obrazu](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service). Další služby, včetně služeb třetích stran, jsou k dispozici jako rozšíření v [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance).

## <a name="diagnosing-problems-in-the-cloud"></a>Diagnostikování problémů v cloudu
Jakmile nasadíte aplikaci do Azure, můžete se setkat s případy, kdy pracovaly ve vývoji, ale ne v Azure. Níže najdete dvě místa, kde se spouští při diagnostice problémů:

* **Vzdálený ladění ze sady Visual Studio**: většina výpočetních služeb Azure (včetně služeb popsaných v tomto dokumentu) podporuje vzdálené ladění pomocí sady Visual Studio a získávání protokolů. Pokud chcete prozkoumat možnosti sady Visual Studio s vaší aplikací, otevřete okno nástroje Průzkumník cloudu zadáním ' Průzkumník cloudu ' do panelu nástrojů snadného spuštění sady Visual Studio (v pravém horním rohu) a pak vyhledejte aplikaci ve stromu. Podrobnosti najdete v tématu [řešení potíží s webovou aplikací v Azure App Service pomocí sady Visual Studio](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).

* **Application Insights**: [Application Insights](https://docs.microsoft.com/azure/application-insights/) je kompletní řešení APM (Application Performance Monitoring), které zachycuje data diagnostiky, telemetrie a výkonu z aplikací automaticky. Pokud chcete začít shromažďovat diagnostická data pro vaši aplikaci, přečtěte si téma [zahájení monitorování webové aplikace v ASP.NET](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal).

## <a name="next-steps"></a>Další kroky

* [Nasazení první ASP.NET Core webové aplikace do Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)
* [Další informace o ověřování v sadě Azure SDK pro .NET](./sdk/authentication.md)
* [Diagnostika chyb v cloudových aplikacích](https://devblogs.microsoft.com/aspnet/diagnosing-errors-on-your-cloud-apps/)
* Stažení bezplatné elektronické knihy [Azure úvodní příručka pro vývojáře na platformě .NET](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook)
