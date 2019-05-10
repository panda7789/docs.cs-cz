---
title: 'Uvnitř CustomPeerResolverService: Registrace klienta'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 3d1e1c6493da54bc3ae0e74a33985da59382ea52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619784"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Uvnitř CustomPeerResolverService: Registrace klienta
Každý uzel v mřížce publikuje jeho informace o koncovém bodu k službě překládání prostřednictvím `Register` funkce. Tyto informace službě překládání ukládá jako registrační záznam. Tento záznam obsahuje jedinečný identifikátor (RegistrationID) a informace o koncovém bodu (PeerNodeAddress) pro uzel.  
  
## <a name="stale-records-and-expiration-time"></a>Zastaralých záznamů a čas vypršení platnosti  
 V ideálním případě Jestliže uzel opustí síť, bude volat `Unregister` funkce, která způsobí, že služba překladač odebrat položku registrace. V některých případech uzly vypnutý nebo není přístupný před voláním `Unregister`, odejít ze za zastaralé registrační záznam.  
  
 Zastaralé záznamy ve službě překládání může způsobit selhání připojení. Pokud uzel pokusu o připojení do sítě obdrží informace o zastaralých připojení ze služby překladače, může trvat delší dobu úspěšně připojit síť. Paměť spotřebovávat také zastaralých záznamů. Bez efektivní vyčistit procesu je mezipaměť používaná k ukládání registrace může nakonec přetečení a chybách u aplikací službě překládání.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Označí každý záznam se čas vypršení platnosti (DateTime) a ukládá tyto informace v rámci záznamu. Služba používá k identifikaci zastaralých záznamů čas vypršení platnosti. Vlastní implementace by měl udělat něco podobného.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval a CleanupInterval  
 `RefreshInterval` Vlastnost <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> definuje, jak dlouho jsou dál platné ve vyhledávací tabulce registrace služby záznamy registrace. Po uplynutí množství času zadaný pro tuto vlastnost pro daný záznam, že záznam zastarávají a je označená k odstranění.  
  
 `CleanupInterval` Vlastnost <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> jak často službě řekne Hledat a odstraňovat záznamy zastaralých registrace. `CleanupInterval` Musí být nastavená na čas větší než nebo rovna hodnotě `RefreshInterval` nastavit služby.  
  
 K implementaci překladače služby, budete muset napsat funkci údržby odebrat záznamy zastaralých registrace. Chcete-li to provést několika způsoby:  
  
- **Pravidelná údržba**: Nastavte časovač pravidelně přejdete a procházení úložiště dat. Chcete-li odstranit staré záznamy. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Používá tuto metodu.  
  
- **Pasivní odstranění**: Nemusíte aktivně hledat zastaralých záznamů v pravidelných intervalech, můžete určit a odstranit zastaralé záznamy, když vaše služba již probíhá jiné funkci. To může potenciálně zapříčinit zpomalení doby odezvy na požadavky od klientů překladače, ale eliminuje potřebu časovač a efektivnější, pokud jsou několika uzlů očekávat, chcete stránku opustit bez volání `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime a aktualizace  
 Jakmile se uzel zaregistruje překladač služby, začne přijímat <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> objekt ze služby. Zda má tento objekt `RegistrationLifetime` vlastnost, která označuje k uzlu, jak dlouho má před registraci platnost a odebere ve službě překládání. Pokud například `RegistrationLifetime` činí 2 minuty, uzlu je potřeba volat `Refresh` v záznamu zůstává čerstvé a není odstraněn, v části 2 minuty. Když se obdrží službě překládání `Refresh` vyhledá záznam a obnoví čas vypršení platnosti požadavku. Aktualizovat vrátí <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> objektu `RegistrationLifetime` vlastnost.  
  
## <a name="see-also"></a>Viz také:

- [Překladače partnerských uzlů](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
