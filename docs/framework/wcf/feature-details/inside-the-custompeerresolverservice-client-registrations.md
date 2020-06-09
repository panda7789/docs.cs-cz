---
title: 'Uvnitř CustomPeerResolverService: registrace klienta'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: ce694408edbb40309d1750be49b8414ebcbce3f7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596835"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>Uvnitř CustomPeerResolverService: registrace klienta
Každý uzel v síti publikuje informace o koncových bodech do služby překladače prostřednictvím `Register` funkce. Služba překladače ukládá tyto informace jako registrační záznam. Tento záznam obsahuje jedinečný identifikátor (RegistrationID) a informace o koncovém bodu (PeerNodeAddress) pro uzel.  
  
## <a name="stale-records-and-expiration-time"></a>Zastaralé záznamy a čas vypršení platnosti  
 V ideálním případě, když uzel opustí síť, zavolá `Unregister` funkci, která způsobí, že služba překladače odebere položku registrace. V některých případech se uzly před voláním ukončí nebo nebudou přístupné `Unregister` , a to za zastaralým registračním záznamem.  
  
 Zastaralé záznamy ve službě překladače můžou způsobit neúspěšná připojení. Pokud uzel, který se pokouší připojit k síti, obdrží zastaralé informace o připojení ze služby překladače, může trvat déle, než se úspěšně připojí k síti. Zastaralé záznamy také zabírají paměť. Bez efektivního procesu vyčištění by mohla mezipaměť používaná k uložení registrů nakonec přetečení a zhroucení služby překladače.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>Označuje každý záznam s časem vypršení platnosti (DateTime) a ukládá tyto informace jako součást záznamu. Služba používá čas vypršení platnosti k identifikaci zastaralých záznamů. Vlastní implementace by měly dělat něco podobného.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>Třídy RefreshInterval a CleanupInterval  
 `RefreshInterval`Vlastnost <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> definuje, jak dlouho budou registrační záznamy v tabulce vyhledávání registrace služby platné. Po předání doby do této vlastnosti u daného záznamu se tento záznam zastará a označí pro odstranění.  
  
 `CleanupInterval`Vlastnost <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> oznamuje službě, jak často se mají vyhledávat a odstraňovat zastaralé záznamy o registraci. `CleanupInterval`Měl by být nastaven na čas, který je větší nebo roven `RefreshInterval` sadě nastavené ve službě.  
  
 Chcete-li implementovat vlastní službu překladače, je nutné zapsat funkci údržby pro odebrání zastaralých záznamů registrace. To lze provést několika způsoby:  
  
- **Pravidelná údržba**: nastavte časovač pro pravidelné vypínání a přecházejte přes úložiště dat a odstraňte staré záznamy. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>Používá tento přístup.  
  
- **Pasivní odstranění**: místo aktivního hledání zastaralých záznamů v pravidelných intervalech můžete identifikovat a odstranit zastaralé záznamy, i když vaše služba již provádí jinou funkci. To může potenciálně zpomalit odezvu na žádosti od klientů překladače, ale eliminuje nutnost časovače a může být efektivnější, pokud se očekává, že zbývá jenom několik uzlů bez volání `Unregister` .  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime a aktualizovat  
 Když se uzel registruje pomocí služby překladače, obdrží <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> objekt ze služby. Tento objekt má `RegistrationLifetime` vlastnost, která určuje, jak dlouho má uzel čas před vypršením platnosti registrace a který je odebrán službou překladače. Pokud `RegistrationLifetime` je například 2 minuty, musí uzel zavolat za `Refresh` 2 minuty, aby bylo zajištěno, že záznam zůstane v čerstvém stavu a nebude odstraněn. Když služba resolver obdrží `Refresh` požadavek, vyhledá záznam a obnoví čas vypršení platnosti. Funkce Refresh vrátí <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> objekt s `RegistrationLifetime` vlastností.  
  
## <a name="see-also"></a>Viz také

- [Překladače partnerských uzlů](peer-resolvers.md)
