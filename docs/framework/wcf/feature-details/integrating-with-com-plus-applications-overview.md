---
title: "Integrace s aplikacemi modelu COM+ – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fbed530a1b968bb049ee20262eb2b8fa9ba13c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications-overview"></a>Integrace s aplikacemi modelu COM+ – přehled
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje bohaté prostředí pro vytváření distribuované aplikace. Pokud už používáte logiku aplikace založené na součást hostované v modelu COM +, můžete použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozšířit existující logiky, místo aby ho přepsání. Obvyklým scénářem je, když chcete vystavit existující modelu COM + nebo podnikové služby obchodní logiky přes webové služby.  
  
 Pokud jako webové služby je vystavený rozhraní komponenty modelu COM +, specifikace a kontrakt tyto služby jsou určeny automatické mapování, které se provádí v době inicializace aplikace. Následující seznam uvádí konceptuálního modelu pro toto mapování:  
  
-   Pro každý zveřejněné třídy COM není definován jedna služba.  
  
-   Kontrakt služby je odvozený přímo z definice vybrané součásti rozhraní s možností metoda vyloučení definované v konfiguraci.  
  
-   Operace v této smlouvě jsou odvozeny přímo z metod v definici rozhraní součásti.  
  
-   Parametry pro tyto operace jsou odvozeny přímo z typ vzájemná funkční spolupráce COM, který odpovídá parametry metody součásti.  
  
 Výchozí adresy a přenosu vazeb pro služby jsou uvedeny v konfiguračním souboru služby, ale to může být překonfigurovaný jako vyžaduje.  
  
> [!NOTE]
>  Kontrakty zveřejněné webových služeb zůstat konstantní tak dlouho, dokud se rozhraní modelu COM + a konfigurace zůstanou beze změny. Úpravy na několik rozhraní automaticky neaktualizuje dostupné služby a vyžaduje znovu spustit nástroj COM + Service Model Configuration (ComSvcConfig.exe).  
  
 Požadavky na ověřování a autorizace aplikace modelu COM + a jeho součástí nadále vynutit, pokud se používá jako webovou službu.  
  
 Iniciuje-li volající transakce webové služby, součásti, které jsou označeny jako transakční zařazení v rámci oboru této transakce.  
  
 Následující kroky jsou nezbytné pro vystavení komponenty modelu COM + rozhraní jako webovou službu beze změny komponentu:  
  
1.  Určí, zda rozhraní komponenty modelu COM + mohou být zpřístupněny jako webovou službu.  
  
2.  Vyberte odpovídající hostování režim.  
  
3.  Přidat webovou službu pro rozhraní pomocí nástroje modelu COM + Service Model Configuration (ComSvcConfig.exe). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]použít ComSvcConfig.exe najdete v tématu [postupy: použití modelu COM + Service Model Configuration Tool](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4.  Nakonfigurujte nastavení žádné další služby v konfiguračním souboru aplikace. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurace součásti najdete v tématu [postupy: Konfigurace služby nastavení modelu COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Podporované rozhraní  
 Existují některá omezení na typu rozhraní, které mohou být zpřístupněny jako webovou službu. Nejsou podporovány následující typy rozhraní:  
  
-   Rozhraní, která odkazuje na objekt předat jako parametry - je následující postup omezené objekt odkaz v části omezenou podporu odkaz na objekt popsané.  
  
-   Rozhraní, které předávají typy, které nejsou kompatibilní s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] převody vzájemná funkční spolupráce COM.  
  
-   Rozhraní pro aplikace, které mají sdružování aplikací povolit, když je hostitelem modelu COM +.  
  
-   Rozhraní komponent, které jsou označeny jako privátní k aplikaci.  
  
-   Infrastruktura rozhraní modelu COM +.  
  
-   Rozhraní z aplikace v systému.  
  
-   Rozhraní z podnikové služby komponent, které nebyly přidané do globální mezipaměti sestavení.  
  
### <a name="limited-object-reference-support"></a>Odkaz na podporu omezené objektu  
 Vzhledem k tomu, že počet nasazené komponenty modelu COM + objekty použít odkaz na parametry, jako je například objekt sady záznamů ADO integrace COM + obsahuje omezenou podporu pro parametry odkaz na objekt. Podpora je omezena na objekty, které implementují `IPersistStream` rozhraní modelu COM. To zahrnuje objekty sady záznamů ADO a může být implementováno pro konkrétní objekty COM aplikací.  
  
 Chcete-li povolit tuto podporu, poskytuje nástroj ComSvcConfig.exe **allowreferences** přepínač, který zakáže parametru podpis regulární metody a zkontroluje, zda je nástroj spuštěn zajistit nejsou používány parametry odkaz na objekt . Kromě toho musí být typy objektů, které můžete předat jako parametry s názvem a identifikovat v rámci <`persistableTypes`> Konfigurace element, který je podřízená <`comContract`> elementu.  
  
 Při použití této funkce, používá služba integrace COM + `IPersistStream` rozhraní k serializaci nebo deserializaci instance objektu. Pokud instance objektu nepodporuje `IPersistStream`, je vyvolána výjimka.  
  
 V rámci klientské aplikace, metody na <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> objekt lze předat objekt v služby a podobně načíst objekt.  
  
> [!NOTE]
>  Z důvodu povaze specifické pro platformu a vlastní serializace přístup, to je nejvhodnější pro použití mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
## <a name="selecting-the-hosting-mode"></a>Výběr hostování režimu  
 Modelu COM + zpřístupní webové služby v jednom z následujících režimů hostingu:  
  
-   Modelu COM +-hostované  
  
     Webová služba je hostována v rámci aplikace vyhrazené modelu COM + procesu serveru (Dllhost.exe). Tento režim vyžaduje, aby aplikace explicitně spustit předtím, než mohl přijímat žádosti webové služby. Modelu COM + možnosti "Spustit jako služba NT" nebo "Ponechejte spuštění při nečinnosti" lze zabránit nečinnosti, po vypnutí aplikace a jeho služeb. Tento režim poskytuje webové služby a modelu DCOM přístup k aplikaci serveru.  
  
-   Hostované Web  
  
     Webová služba je hostována v rámci pracovní proces webového serveru. Tento režim nevyžaduje modelu COM + být active, když je obdržena úvodního požadavku. Pokud aplikace není aktivní, když je obdržena tuto žádost, se automaticky aktivuje před zpracování požadavku. Tento režim taky poskytuje webové služby a přístup k DCOM pro serverové aplikace, ale způsobí, že proces směrování pro žádosti webové služby. To obvykle vyžaduje, aby klient k povolení zosobnění. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], to lze provést pomocí <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třídy, která je přístupná jako vlastnost obecná <xref:System.ServiceModel.ChannelFactory%601> třída, společně s <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> hodnota výčtu.  
  
-   Web hostovaný v procesu  
  
     Webové služby a logiku aplikace modelu COM + jsou hostované v rámci pracovní proces webového serveru. To umožňuje automatické aktivace režimu hostované webové aniž by to způsobilo procesu směrování pro žádosti webové služby. Nevýhodou je, že je serverová aplikace není umožněn přístup přes DCOM.  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Stejně jako jiné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služeb, nastavení zabezpečení pro službu zveřejněné jsou spravovány pomocí nastavení konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanálu. Tradiční nastavení zabezpečení DCOM např. nastavení modelu DCOM oprávnění celého systému nejsou vynucená. Pokud chcete vynutit role aplikací modelu COM +, musí být povolena "přístup na úrovni součásti kontroly" autorizace pro komponentu.  
  
 Použití vazby zabezpečené můžete nechat komunikace otevřené manipulaci nebo informace o zpřístupnění. Chcete-li tomu zabránit, doporučujeme použít zabezpečené vazby.  
  
 Pro modelu COM +-hostované a webové hostované režimy klientské aplikace musí povolit proces serveru zosobnění uživatele klienta. To lze provést [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů podle nastavení úrovně k zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Pomocí Internetové informační služby (IIS) nebo proces aktivace služby WAS (Windows) pomocí přenosového protokolu HTTP nástroje Httpcfg.exe lze rezervovat adresu koncového bodu přenosu. V další konfigurace je důležité pro ochranu proti podvodným služby, které fungují jako služba určený. Abyste zabránili začínající na požadovaný koncový bod služby podvodný, legitimní službu lze nakonfigurovat pro spuštění jako služba NT. To umožňuje oprávněné službě deklarace identity adresa koncového bodu před žádné podvodný služby.  
  
 Při zpřístupnění aplikace modelu COM + s nakonfigurovanou rolí modelu COM + jako hostované webové služby, "spuštění služby IIS proces" musí být účet přidaný do jednoho z role aplikace. Tento účet, obvykle s názvem IWAM_machinename, musíte přidat do povolit čistého vypnutí objektů po použití. Účet by neměla být udělena žádná další oprávnění.  
  
 Funkce recyklace procesu modelu COM + nelze použít na integrovaných aplikací. Pokud aplikace je nakonfigurovaná pro použití recyklace procesů a komponenty běží v procesu hostované modelu COM +, službu nepodaří spustit. Tento požadavek nezahrnuje služby pomocí režimu Web hostovaný v rámci procesu, protože proces recyklace nastavení se nepoužijí.  
  
## <a name="see-also"></a>Viz také  
 [Přehled integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
