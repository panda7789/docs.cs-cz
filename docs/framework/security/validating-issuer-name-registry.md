---
title: Registr pro ověřování názvů vydavatelů
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: fc10181a142fd8ca4ebd8250869d49a046623564
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910783"
---
# <a name="validating-issuer-name-registry"></a>Registr pro ověřování názvů vydavatelů
Pomocí rozšíření Validating Issuer Name Registry (VINR) pro technologii Windows Identity Foundation mohou víceklientské aplikace zjišťovat, zda byl příchozí token vystaven důvěryhodným klientem a poskytovatelem identity. Tato funkce je zvláště užitečná pro víceklientské aplikace, které používají službu Microsoft Azure Active Directory, protože všechny tokeny vystavené službou Microsoft Azure AD jsou podepsány pomocí stejného certifikátu. Aby bylo možné rozlišovat mezi žádostmi od různých klientů, kteří používají stejný certifikát (a mají tedy také stejný kryptografický otisk), musí vaše aplikace pro každého klienta uchovat jméno vystavitele pro účely logiky ověřování. Rozšíření VINR zajišťuje tuto funkci a umožňuje také přidat vlastní logiku ověřování nebo ukládat data registru vystavitelů v jiných umístěních než v konfiguračním souboru. Toto rozšíření lze přidat do kanálu WIF aplikace nebo je lze používat samostatně.  
  
 Rozšíření VINR je k dispozici jako balíček NuGet. Zobrazit [stažení balíčku registru ověřování názvů vydavatelů](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) Další informace.  
  
## <a name="scenarios"></a>Scénáře  
 Rozšíření VINR podporuje následující klíčový scénář:  
  
- **Ověření tokenu ve víceklientské aplikaci**: V tomto scénáři vyvinula společnost s názvem Litware víceklientskou aplikaci, která používá poskytovatele identit, jako je například Windows Azure AD. Tato aplikace slouží dvěma zákazníkům: Contoso a Fabrikam. Když se uživatel ze společnosti Fabrikam ověřuje vůči aplikaci společnosti Litware, je výsledný token ze služby Microsoft Azure AD podepsán pomocí jejího standardního certifikátu a žádost podává společnost Fabrikam. Aplikace musí ověřit, zda jsou název vystavitele i token platné, a musí rozlišovat žádosti od společnosti Contoso, které jsou podepsány pomocí stejného certifikátu služby Microsoft Azure AD. Pomocí rozšíření VINR může aplikace společnosti Litware snadno rozlišit a ověřit žádosti od různých klientů, jako jsou společnosti Contoso a Fabrikam.  
  
## <a name="features"></a>Funkce  
 Rozšíření VINR nabízí následující funkce:  
  
- **Název vystavitele a ověřování tokenů pro víceklientské aplikace**: Ověřuje příchozí tokeny tak, že ověříte název vystavitele (klienta) a určuje, zda byl token podepsán pomocí platného certifikátu od poskytovatele identity.  
  
- **Rozšiřitelnost pro vlastní logiku ověřování a úložiště dat**: Poskytuje rozšíření vkládat vlastní logiku ověřování a k určení úložiště dat než výchozí konfigurační soubor.
