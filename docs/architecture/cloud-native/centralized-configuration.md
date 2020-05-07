---
title: Centralizovaná konfigurace
description: Centralizace konfigurace pro cloudové aplikace s využitím konfigurace aplikací Azure a trezoru AzureKey.
ms.date: 04/19/2020
ms.openlocfilehash: 53bdc03370b04af4d830fe7abbd8aebad81e9650
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895657"
---
# <a name="centralized-configuration"></a>Centralizovaná konfigurace

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Na rozdíl od aplikace monolitické, ve které se všechno spouští v rámci jedné instance, se aplikace Cloud Native skládá z nezávislých služeb distribuovaných napříč virtuálními počítači, kontejnery a geografickými oblastmi. Správa nastavení konfigurace pro desítky vzájemně závislých služeb může být náročná. Duplicitní kopie nastavení konfigurace v různých umístěních jsou náchylné k chybám a jsou obtížně spravované. Centralizovaná konfigurace je zásadním požadavkem pro distribuované aplikace nativní pro Cloud.

Jak je popsáno v [kapitole 1](introduction.md), doporučení pro dvanácti s aplikacemi vyžadují striktní oddělení mezi kódem a konfigurací. Konfigurace musí být ukládána externě z aplikace a v případě potřeby je lze přečíst. Ukládání hodnot konfigurace jako konstanty nebo hodnoty literálů v kódu je porušení. Stejné hodnoty konfigurace často používá mnoho služeb ve stejné aplikaci. Kromě toho je potřeba podporovat stejné hodnoty v různých prostředích, jako je vývoj, testování a produkce. Osvědčeným postupem je ukládat je do centralizovaného úložiště konfigurace.

Cloud Azure nabízí několik skvělých možností.

## <a name="azure-app-configuration"></a>Azure App Configuration

[Konfigurace aplikací Azure](https://docs.microsoft.com/azure/azure-app-configuration/overview) je plně spravovaná služba Azure, která ukládá nastavení konfigurace bez tajných klíčů do zabezpečeného, centralizovaného umístění. Uložené hodnoty lze sdílet mezi více službami a aplikacemi.

Služba se snadno používá a přináší několik výhod:

- Flexibilní reprezentace klíč/hodnota a mapování
- Označování pomocí popisků Azure
- Vyhrazené uživatelské rozhraní pro správu
- Šifrování citlivých informací
- Dotazování a dávkové načítání

Konfigurace aplikace Azure udržuje změny nastavení klíč-hodnota po dobu sedmi dnů. Funkce snímku v čase umožňuje rekonstruovat historii nastavení a dokonce i vrácení neúspěšného nasazení.

Konfigurace aplikace automaticky ukládá do mezipaměti každé nastavení, aby nedocházelo k nadměrným voláním do úložiště konfigurace. Operace aktualizace počká, dokud nevyprší hodnota nastavení uložené v mezipaměti, a to i v případě, že se změní hodnota v úložišti konfigurace. Výchozí doba vypršení platnosti mezipaměti je 30 sekund. Můžete přepsat čas vypršení platnosti.

Konfigurace aplikace šifruje všechny hodnoty konfigurace v cestě a v klidovém režimu. Názvy klíčů a popisky se používají jako indexy pro načítání konfiguračních dat a nejsou zašifrované.

I když konfigurace aplikace poskytuje zesílené zabezpečení, Azure Key Vault je stále nejlepším místem pro ukládání tajných klíčů aplikací. Key Vault poskytuje šifrování na úrovni hardwaru, podrobné zásady přístupu a operace správy, jako je například rotace certifikátu. Můžete vytvořit konfigurační hodnoty aplikace, které odkazují na tajné kódy uložené v Key Vault.

## <a name="azure-key-vault"></a>Azure Key Vault

Key Vault je spravovaná služba pro bezpečné ukládání a přístup k tajným klíčům. Tajný klíč je cokoli, k čemu chcete pečlivě kontrolovat přístup, třeba klíče rozhraní API, hesla nebo certifikáty. Trezor je logická skupina tajných kódů.

Key Vault výrazně snižuje riziko nechtěného úniku tajných klíčů. Při použití služby Key Vault už vývojáři aplikací nemusejí ukládat informace o zabezpečení ve svých aplikacích. Tento postup eliminuje potřebu ukládat tyto informace ve vašem kódu. Aplikace se například může potřebovat připojit k databázi. Místo uložení připojovacího řetězce v kódu aplikace ho můžete bezpečně uložit do Key Vault.

Vaše aplikace můžou zabezpečeně přistupovat k informacím, které potřebují, pomocí identifikátorů URI. Tyto identifikátory URI umožňují aplikacím načíst konkrétní verze tajného kódu. Není nutné psát vlastní kód pro ochranu jakýchkoli tajných informací uložených v Key Vault.

Přístup k Key Vault vyžaduje správné ověření volajícího a autorizaci. Obvykle každá mikroslužba nativního cloudu používá kombinaci ClientId/ClientSecret. Je důležité zachovat tyto přihlašovací údaje mimo správu zdrojového kódu. Osvědčeným postupem je nastavení v prostředí aplikace. Přímý přístup k Key Vault z AKS lze dosáhnout pomocí [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol).

## <a name="configuration-in-eshop"></a>Konfigurace v eShop

Aplikace eShopOnContainers zahrnuje místní soubory nastavení aplikace s každou mikroslužbou. Tyto soubory jsou zkontrolovány do správy zdrojového kódu, ale nezahrnují provozní tajemství, jako jsou připojovací řetězce nebo klíče rozhraní API. V produkčním prostředí může být individuální nastavení přepsáno pomocí proměnných prostředí pro jednotlivé služby. Vkládání tajných kódů v proměnných prostředí je běžné postupy pro hostované aplikace, ale neposkytuje centrální úložiště konfigurace. V rámci podpory centralizované správy nastavení konfigurace každá mikroslužba obsahuje nastavení, které se přepíná mezi použitím místních nastavení nebo nastavení Azure Key Vault.

## <a name="references"></a>Odkazy

- [Architektura eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [Orchestrace mikroslužeb a vícekontejnerových aplikací pro vysokou škálovatelnost a dostupnost](https://docs.microsoft.com/dotnet/architecture/microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications)
- [Azure API Management](https://docs.microsoft.com/azure/api-management/api-management-key-concepts)
- [Přehled Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)
- [Azure Cache for Redis](https://azure.microsoft.com/services/cache/)
- [Rozhraní API služby Azure Cosmos DB pro MongoDB](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Přehled služby Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)
- [eShopOnContainers: Vytvoření clusteru Kubernetes v AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Předchozí](deploy-eshoponcontainers-azure.md)
>[Další](scale-applications.md)
