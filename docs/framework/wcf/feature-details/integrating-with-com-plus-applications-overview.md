---
title: Integrace s aplikacemi modelu COM+ – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: fbe27403920d8c85665e585ca461602131574038
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638638"
---
# <a name="integrating-with-com-applications-overview"></a>Integrace s aplikacemi modelu COM+ – přehled
Windows Communication Foundation (WCF) poskytuje bohaté prostředí pro vytváření distribuované aplikace. Pokud už používáte založených na komponentách aplikační logiky, které jsou hostované v modelu COM +, můžou využít WCF k rozšíření existující logic namísto nutnosti jeho přepsání. Běžný scénář, kdy je, když chcete vystavit existujícího modelu COM + nebo podnikové služby obchodní logiky pomocí webové služby.  
  
 Při vystavení rozhraní komponenty COM + jako webovou službu, specifikace a smlouvy z těchto služeb jsou určeny automatické mapování, která se provede v době inicializace aplikace. Následující seznam ukazuje koncepční model pro toto mapování:  
  
- Pro každou třídu vystavených modelu COM je definována jednu službu.  
  
- Kontrakt služby je odvozen přímo z definice rozhraní vybrané součásti s možností metoda vyloučení definované v konfiguraci.  
  
- Operace v této smlouvy jsou odvozena přímo z metod v definici rozhraní komponenty.  
  
- Parametry pro tyto operace jsou odvozena přímo z typu vzájemná funkční spolupráce modelu COM, která odpovídá na parametry metod komponenty.  
  
 Výchozí adresy a vazby přenosu pro služby v konfiguračním souboru služby. Pokud ale tyto dají nakonfigurovat tak, jako povinné.  
  
> [!NOTE]
>  Kontrakty pro ohrožené webové služby zůstal neměnný tak dlouho, dokud rozhraní modelu COM + a konfigurace zůstanou beze změny. Úpravy několik rozhraní se neaktualizuje automaticky dostupné služby a vyžaduje znovu spustit nástroj COM + Service Model Configuration (ComSvcConfig.exe).  
  
 Požadavky na ověřování a autorizace aplikace modelu COM + a jeho součástí i nadále vynucovat, když se použije jako webovou službu.  
  
 Iniciuje-li volající transakce webové služby, součásti označeny jako transakční zařazení v daném oboru transakce.  
  
 Následující kroky jsou nutné k vystavení rozhraní komponenty modelu COM + jako webovou službu beze změny komponenty:  
  
1. Určení, zda rozhraní komponenty modelu COM + může být vystavena jako webové služby.  
  
2. Vyberte odpovídající hostující režim.  
  
3. Použijte nástroj pro konfiguraci modelu služby COM + (ComSvcConfig.exe) Chcete-li přidat webovou službu pro rozhraní. Další informace o tom, jak používat ComSvcConfig.exe najdete v tématu [jak: Použijte nástroj pro konfiguraci modelu služby COM +](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4. Konfigurace nastavení jakékoli další služby v konfiguračním souboru aplikace. Další informace o tom, jak nakonfigurovat komponenty, naleznete v tématu [jak: Konfigurace nastavení služby modelu COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Podporované rozhraní  
 Platí určitá omezení na typ rozhraní, která může být vystavena jako webové služby. Nejsou podporovány následující typy rozhraní:  
  
- Rozhraní, která předat objekt odkazy jako parametry - následující odkaz přístup omezený objektu je popsané v části omezená podpora odkaz na objekt.  
  
- Rozhraní, které předávají typy, které nejsou kompatibilní s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] převody vzájemná funkční spolupráce modelu COM.  
  
- Rozhraní pro aplikace, které mají aplikace sdružování povolena, když jsou hostované pomocí modelu COM +.  
  
- Rozhraní komponent, které jsou označeny jako soukromé do aplikace.  
  
- Infrastruktura rozhraní modelu COM +.  
  
- Rozhraní z aplikace v systému.  
  
- Rozhraní služby Enterprise součásti, které se nepřidaly do globální mezipaměti sestavení.  
  
### <a name="limited-object-reference-support"></a>Podpora odkaz omezené objektu  
 Protože počet nasazených komponenty COM +. můžete použít objekty odkaz parametry, jako je například vrací objekt sady záznamů ADO integrace modelu COM + obsahuje omezenou podporu pro parametry objektů reference. Podpora je omezena na objekty, které implementují `IPersistStream` rozhraní modelu COM. To zahrnuje objekty sady záznamů ADO a může být implementováno pro objekty COM. konkrétní aplikace.  
  
 Pokud chcete povolit tuto podporu, poskytuje nástroj ComSvcConfig.exe **allowreferences** přepínač, který zakáže v parametru signatury metody regulárních a ověří, že je nástroj spuštěn zajistit, že parametry objektů reference nejsou používány. . Kromě toho musí být typy objektů, které se předávají jako parametry s názvem a identifikovat v rámci <`persistableTypes`> Konfigurace element, který je podřízeným prvkem <`comContract`> element.  
  
 Při použití této funkce, používá služba integrace modelu COM + `IPersistStream` rozhraní k serializaci nebo deserializaci instance objektu. Pokud se instance objektu nepodporuje `IPersistStream`, je vyvolána výjimka.  
  
 V rámci klientské aplikace, metody <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> objekt lze použít k předání objektu v ke službě a podobně pro načtení objektu.  
  
> [!NOTE]
>  Protože potřebujeme specifické pro platformu a vlastní serializace přístup to je nejvhodnější pro použití mezi klienty WCF a služby WCF.  
  
## <a name="selecting-the-hosting-mode"></a>Hostující režim výběru  
 COM + zveřejňuje webové služby v jednom z následujících režimů hostingu:  
  
- COM +.-hostované  
  
     Webová služba je hostována v rámci aplikace vyhrazené modelu COM + procesu serveru (Dllhost.exe). Tento režim vyžaduje aplikace explicitně spustit předtím, než může přijímat žádosti webové služby. COM + možnosti "Spustit jako služba NT" nebo "Ponechte spuštěna při nečinnosti" je možné zabránit ukončení aplikace a její služby při nečinnosti. Tento režim poskytuje webovou službu a přístup k DCOM na server aplikace.  
  
- Hostované webové  
  
     Webová služba je hostována v rámci pracovní proces webového serveru. Tento režim nevyžaduje modelu COM + jako aktivní po přijetí počáteční požadavek. Pokud aplikace není aktivní, při přijetí tohoto požadavku, se automaticky aktivuje před zpracováním žádosti. Tento režim také poskytuje webovou službu a přístup k DCOM pro serverové aplikace, ale způsobí, že proces směrování webových žádostí o službu. Obvykle vyžaduje povolení zosobnění klienta. Ve službě WCF, to lze provést pomocí <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> třídy, které je přístupné jako vlastnost Obecné <xref:System.ServiceModel.ChannelFactory%601> třídu, stejně jako <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> hodnota výčtu.  
  
- Web hostovaný v procesu  
  
     Webové služby a logika aplikace modelu COM + jsou hostovány v rámci pracovní proces webového serveru. Tímto způsobem automatickou aktivaci režimu hostované webové bez způsobení procesu směrování webových žádostí o službu. Nevýhodou je, že serverová aplikace není možné přistupovat prostřednictvím modelu DCOM.  
  
### <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Stejně jako jiné služby WCF nastavení zabezpečení pro službu vystavené spravují nastavení konfigurace pro kanál WCF. Tradiční nastavení zabezpečení DCOM, například nastavení celý počítač oprávnění modelu DCOM nevynucují. K vynucení aplikační role COM +, musí být povoleno "kontroly přístupu na úrovni součástí" autorizace pro komponenty.  
  
 Použití nezabezpečené vazby můžete nechat komunikaci otevřené manipulaci nebo informace o zpřístupnění. Chcete-li tomu zabránit, doporučujeme použít zabezpečené vazby.  
  
 Modelu COM +-režimy hostované a hostuje Web, klientské aplikace musí povolit procesu server zosobnit uživatele klienta. To můžete udělat v klientech WCF, tak, že nastavíte na úrovni zosobnění <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Internetové informační služby (IIS) nebo Windows WAS Process Activation Service () pomocí přenos pomocí protokolu HTTP nástroje Httpcfg.exe lze rezervovat adresa koncového bodu přenosu. V další konfigurace je důležité pro ochranu proti podvodným služby, které plnit funkci určené služby. Abyste zabránili podvodné službě začínají na požadovaný koncový bod, legitimní službu lze nakonfigurovat ke spuštění jako služba NT. To umožňuje službě legitimní chcete uplatnit nárok na adresu koncového bodu před všechny neautorizovaných serverů služby.  
  
 Při vystavení aplikace modelu COM + s nakonfigurovanou rolí COM +. jako hostované webové služby, "Spuštění služby IIS účet procesu" musí být přidány do jedné z rolí aplikace. Tento účet, obvykle s názvem IWAM_machinename musí přidat k povolení čistého vypnutí objektů po použití. Účet by neměla mít udělen žádná další oprávnění.  
  
 Funkce recyklace procesů modelu COM + nelze použít na integrovaných aplikací. Pokud aplikace je nakonfigurován pro použití recyklace procesů a komponenty běží v procesu hostovány COM +, službu nepodaří spustit. Tento požadavek nezahrnuje služeb pomocí procesu v režimu hostované webové, protože se nepoužijí nastavení recyklace procesů.  
  
## <a name="see-also"></a>Viz také:

- [Přehled integrace s aplikacemi modelu COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
