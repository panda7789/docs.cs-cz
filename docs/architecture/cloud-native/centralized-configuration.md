---
title: Centralizovaná konfigurace
description: Centralizovaná konfigurace pomocí Azure Key Vault může zjednodušit správu nativních aplikací cloudu.
ms.date: 06/30/2019
ms.openlocfilehash: 4c516b6773d913acd71ff06742302e9766a141e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213998"
---
# <a name="centralized-configuration"></a>Centralizovaná konfigurace

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Nativní aplikace v cloudu zahrnují mnohem více spuštěných služeb než tradiční aplikace monolitické s jednou instancí. Správa nastavení konfigurace pro desítky vzájemně závislých služeb může být náročná. to znamená, že centralizované úložiště konfigurace se často implementují pro distribuované aplikace.

Jak je popsáno v [kapitole 1](introduction.md), doporučení pro dvanácti s aplikacemi vyžadují striktní oddělení mezi kódem a konfigurací. To znamená, že ukládání nastavení konfigurace jako konstanty nebo hodnoty literálů v kódu je porušení. Toto doporučení existuje, protože stejný kód by měl být použit ve více prostředích, včetně vývoje, testování, přípravy a výroby. Konfigurační hodnoty se ale budou nejspíš měnit mezi jednotlivými prostředími. Konfigurační hodnoty by tedy měly být uloženy v samotném prostředí, jinak by toto prostředí mělo ukládat do centralizovaného úložiště konfigurace.

Aplikace eShopOnContainers zahrnuje místní soubory nastavení aplikace s každou mikroslužbou. Tyto soubory jsou zkontrolovány do správy zdrojového kódu, ale nezahrnují provozní tajemství, jako jsou připojovací řetězce nebo klíče rozhraní API. V produkčním prostředí může být individuální nastavení přepsáno pomocí proměnných prostředí pro jednotlivé služby. To je běžný postup pro hostované aplikace, ale neposkytuje centrální úložiště konfigurace. V rámci podpory centralizované správy nastavení konfigurace každá mikroslužba obsahuje nastavení, které se přepíná mezi použitím místních nastavení nebo nastavení Azure Key Vault.

## <a name="azure-key-vault"></a>Azure Key Vault

Azure Key Vault poskytuje zabezpečené úložiště tokenů, hesel, certifikátů, klíčů rozhraní API a dalších citlivých tajných klíčů. Přístup k Key Vault vyžaduje správné ověření volajícího a autorizaci, které v případě mikroslužeb eShopOnContainers označuje použití kombinace ClientId/ClientSecret. Nezadávejte tyto přihlašovací údaje do správy zdrojových kódů, ale místo toho je nastavte v prostředí aplikace. Přímý přístup k Key Vault z AKS lze dosáhnout pomocí [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol).

S centralizovanou konfigurací lze nastavení, která platí pro celou aplikaci, jako je například centralizovaný koncový bod protokolování, nastavit jednou a používat v každé části distribuované aplikace. I když by mikroslužby měly být nezávisle na sobě, obvykle se jedná o některé sdílené závislosti, jejichž podrobnosti konfigurace můžou být z centralizovaného úložiště konfigurace přínosné.

>[!div class="step-by-step"]
>[Předchozí](deploy-eshoponcontainers-azure.md)
>[Další](scale-applications.md)
