---
title: "Registr pro ověřování názvů vydavatelů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d131a032aa2747bda83874e8dd744588dfe07dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="validating-issuer-name-registry"></a>Registr pro ověřování názvů vydavatelů
Pomocí rozšíření Validating Issuer Name Registry (VINR) pro technologii Windows Identity Foundation mohou víceklientské aplikace zjišťovat, zda byl příchozí token vystaven důvěryhodným klientem a poskytovatelem identity. Tato funkce je zvláště užitečná pro víceklientské aplikace, které používají službu Microsoft Azure Active Directory, protože všechny tokeny vystavené službou Microsoft Azure AD jsou podepsány pomocí stejného certifikátu. Aby bylo možné rozlišovat mezi žádostmi od různých klientů, kteří používají stejný certifikát (a mají tedy také stejný kryptografický otisk), musí vaše aplikace pro každého klienta uchovat jméno vystavitele pro účely logiky ověřování. Rozšíření VINR zajišťuje tuto funkci a umožňuje také přidat vlastní logiku ověřování nebo ukládat data registru vystavitelů v jiných umístěních než v konfiguračním souboru. Toto rozšíření lze přidat do kanálu WIF aplikace nebo je lze používat samostatně.  
  
 Rozšíření VINR je k dispozici jako balíček NuGet. V tématu [stažení balíčku registru ověřování název vystavitele](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) Další informace.  
  
## <a name="scenarios"></a>Scénáře  
 Rozšíření VINR podporuje následující klíčový scénář:  
  
-   **Ověřit Token v aplikaci víceklientské**: V tomto scénáři vyvinula společnost s názvem Litware víceklientské aplikace, která používá zprostředkovatele identity jako je například Microsoft Azure AD. Aplikace slouží dvěma zákazníkům: Contoso a Fabrikam. Když se uživatel ze společnosti Fabrikam ověřuje vůči aplikaci společnosti Litware, je výsledný token ze služby Microsoft Azure AD podepsán pomocí jejího standardního certifikátu a žádost podává společnost Fabrikam. Aplikace musí ověřit, zda jsou název vystavitele i token platné, a musí rozlišovat žádosti od společnosti Contoso, které jsou podepsány pomocí stejného certifikátu služby Microsoft Azure AD. Pomocí rozšíření VINR může aplikace společnosti Litware snadno rozlišit a ověřit žádosti od různých klientů, jako jsou společnosti Contoso a Fabrikam.  
  
## <a name="features"></a>Funkce  
 Rozšíření VINR nabízí následující funkce:  
  
-   **Název vystavitele a ověření tokenu pro víceklientské aplikace**: ověří příchozí token kontrolou název vystavitele (klientů) a jestli byl token podepsaný pomocí platný certifikát od zprostředkovatele identity.  
  
-   **Rozšíření pro vlastní ověřovací logiku a Data úložišť**: zajišťuje rozšiřitelnost vložení vlastní logiky ověřování a zadat úložiště dat než výchozí konfigurační soubor.
