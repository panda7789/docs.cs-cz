---
title: 'Uvnitř CustomPeerResolverService: registrace klienta'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 1f8b6f5ac3a41fdc7f817553693b0621ee0ea3de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Uvnitř CustomPeerResolverService: registrace klienta
Každý uzel v mřížce publikuje informace jeho koncový bod, a překladač služby pomocí `Register` funkce. Službu překladač tyto informace ukládá jako registrační záznam. Tento záznam obsahuje jedinečný identifikátor (RegistrationID) a informace o koncovém (PeerNodeAddress) pro uzel.  
  
## <a name="stale-records-and-expiration-time"></a>Zastaralých záznamů a čas vypršení platnosti  
 V ideálním případě Jestliže uzel opustí OK, se bude volat `Unregister` funkce, což způsobí, že služba překladač pro odebrání položky registrace. V některých případech uzly vypnutý nebo jsou nedostupná před voláním `Unregister`, výstupu za zastaralé registrační záznam.  
  
 Zastaralé záznamy ve službě překladač může způsobit selhání připojení. Pokud uzel se připojujete k mřížku přijme připojení zastaralé informace z překladače služby, může trvat déle, než se úspěšně připojit OK. Zastaralých záznamů také zabírají paměť. Bez efektivní vyčištění procesu může do mezipaměti se používá k ukládání registrace nakonec přetečení a havárií službu překladač.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Označí všechny záznamy s vypršení platnosti času (DateTime) a ukládá tyto informace v rámci záznamu. Služba používá k identifikaci zastaralých záznamů čas vypršení platnosti. Vlastní implementace musí udělat něco podobného.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval a CleanupInterval  
 `RefreshInterval` Vlastnost <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> definuje, jak dlouho zůstanou platná ve vyhledávací tabulce registrace služby záznamy registrace. Když množství času, který této vlastnosti byla úspěšná pro daný záznam, že záznam se stane zastaralé a je označena pro odstranění.  
  
 `CleanupInterval` Vlastnost <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> informuje službu jak často k hledání a odstranit záznamy zastaralých registrace. `CleanupInterval` Musí být nastavena na čas větší než nebo rovna hodnotě `RefreshInterval` nastavit služby.  
  
 Chcete-li implementovat vlastní překladač služby, zápis funkce údržby pro odebírání zastaralých registrace záznamů. Chcete-li to provést několika způsoby:  
  
-   **Pravidelná údržba**: nastavit časovač pro přejděte pravidelně vypnout a projít úložiště dat. Chcete-li odstranit staré záznamy. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Používá tento přístup.  
  
-   **Pasivní odstranění**: místo aktivně hledání zastaralých záznamů v pravidelných intervalech, můžete určit a odstranit zastaralé záznamy, když vaše služba již provádí jinou funkci. To může potenciálně prodloužit dobu odezvy na požadavky od klientů překladače, ale eliminuje potřebu časovač a efektivnější, pokud jsou několika uzlů očekávat opustit, aniž volání `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime a aktualizace  
 Uzel zaregistruje překladač službou, obdrží <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> objekt ze služby. Má tento objekt `RegistrationLifetime` vlastnost, která označuje k uzlu, jak dlouho má před registrace vyprší a je odebrán službou překladač. Pokud například `RegistrationLifetime` činí 2 minuty, uzlu potřebuje volat `Refresh` v části 2 minuty zajistit záznam zůstává čerstvé a se neodstraní. Když služba překladač obdrží `Refresh` požádat, vyhledá záznam a obnoví čas vypršení platnosti. Aktualizujte vrátí <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> objektu s `RegistrationLifetime` vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Překladače partnerských uzlů](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
