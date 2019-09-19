---
title: Registr pro ověřování názvů vydavatelů
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: dc7da9d3dc4ab696d8c27d8e12583b8d06e747fe
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045302"
---
# <a name="validating-issuer-name-registry"></a>Registr pro ověřování názvů vydavatelů
Pomocí rozšíření Validating Issuer Name Registry (VINR) pro technologii Windows Identity Foundation mohou víceklientské aplikace zjišťovat, zda byl příchozí token vystaven důvěryhodným klientem a poskytovatelem identity. Tato funkce je zvláště užitečná pro víceklientské aplikace, které používají službu Microsoft Azure Active Directory, protože všechny tokeny vystavené službou Microsoft Azure AD jsou podepsány pomocí stejného certifikátu. Aby bylo možné rozlišovat mezi žádostmi od různých klientů, kteří používají stejný certifikát (a mají tedy také stejný kryptografický otisk), musí vaše aplikace pro každého klienta uchovat jméno vystavitele pro účely logiky ověřování. Rozšíření VINR zajišťuje tuto funkci a umožňuje také přidat vlastní logiku ověřování nebo ukládat data registru vystavitelů v jiných umístěních než v konfiguračním souboru. Toto rozšíření lze přidat do kanálu WIF aplikace nebo je lze používat samostatně.  
  
 Rozšíření VINR je k dispozici jako balíček NuGet. Další informace najdete v tématu [Stažení balíčku registru pro ověření názvu vystavitele](downloading-the-validating-issuer-name-registry-package.md) .  
  
## <a name="scenarios"></a>Scénáře  
 Rozšíření VINR podporuje následující klíčový scénář:  
  
- **Ověření tokenu v aplikaci s více klienty**: V tomto scénáři společnost s názvem Litware vyvinula víceklientské aplikace, která používá poskytovatele identity, jako je například Windows Azure AD. Tato aplikace slouží dvěma zákazníkům: Contoso a Fabrikam. Když se uživatel ze společnosti Fabrikam ověřuje vůči aplikaci společnosti Litware, je výsledný token ze služby Microsoft Azure AD podepsán pomocí jejího standardního certifikátu a žádost podává společnost Fabrikam. Aplikace musí ověřit, zda jsou název vystavitele i token platné, a musí rozlišovat žádosti od společnosti Contoso, které jsou podepsány pomocí stejného certifikátu služby Microsoft Azure AD. Pomocí rozšíření VINR může aplikace společnosti Litware snadno rozlišit a ověřit žádosti od různých klientů, jako jsou společnosti Contoso a Fabrikam.  
  
## <a name="features"></a>Funkce  
 Rozšíření VINR nabízí následující funkce:  
  
- **Název vystavitele a ověření tokenu pro aplikace s více klienty**: Ověří příchozí token tím, že ověří název vystavitele (tenant) a zda byl token podepsán pomocí platného certifikátu od poskytovatele identity.  
  
- **Rozšiřitelnost pro vlastní ověřovací logiku a úložiště dat**: Poskytuje rozšiřitelnost pro vložení vlastní logiky ověřování a určení jiného úložiště dat než výchozí konfigurační soubor.
