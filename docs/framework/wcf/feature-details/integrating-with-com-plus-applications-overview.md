---
title: Integrace s aplikacemi modelu COM+ – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: 57a1537e1bde1efcd3586d032efee063561efcca
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586491"
---
# <a name="integrating-with-com-applications-overview"></a>Integrace s aplikacemi modelu COM+ – přehled
Windows Communication Foundation (WCF) poskytuje bohatou prostředí pro vytváření distribuovaných aplikací. Pokud již používáte aplikační logiku, která je hostována v modelu COM+, můžete použít WCF k rozšiřování stávající logiky, a nemusíte ji přepsat. Běžným scénářem je, že chcete v rámci webové služby vystavit existující obchodní logiku služby COM+ nebo podnikových služeb.  
  
 Pokud je rozhraní komponenty modelu COM+ vystaveno jako webová služba, specifikace a kontrakt těchto služeb jsou určeny automatickým mapováním, které se provádí při inicializaci aplikace. Následující seznam uvádí koncepční model pro toto mapování:  
  
- Jedna služba je definována pro každou vystavenou třídu modelu COM.  
  
- Kontrakt pro službu je odvozen přímo z definice rozhraní vybrané součásti s možností vyloučení metody definované v konfiguraci.  
  
- Operace v tomto kontraktu jsou odvozeny přímo z metod v definici rozhraní komponenty.  
  
- Parametry pro tyto operace jsou odvozeny přímo z typu interoperability modelu COM, který odpovídá parametrům metody komponenty.  
  
 Výchozí adresy a vazby přenosu pro službu jsou k dispozici v konfiguračním souboru služby, ale je možné je v případě potřeby překonfigurovat.  
  
> [!NOTE]
> Smlouvy pro exponované webové služby zůstávají konstantní, dokud rozhraní a konfigurace modelu COM+ zůstanou beze změny. Úprava několika rozhraní neaktualizuje automaticky dostupné služby a vyžaduje opětovné spuštění nástroje pro konfiguraci modelu služby COM+ (ComSvcConfig. exe).  
  
 Požadavky na ověřování a autorizaci aplikace modelu COM+ a jejích komponent se budou při použití jako webové služby nadále vymáhat.  
  
 Pokud volající inicializuje transakci webové služby, komponenty označené jako transakční zařazení v rámci tohoto oboru transakce.  
  
 K vystavení rozhraní komponenty COM+ jako webové služby bez změny součásti se vyžadují následující kroky:  
  
1. Určete, zda je možné rozhraní komponenty modelu COM+ zveřejnit jako webovou službu.  
  
2. Vyberte vhodný hostující režim.  
  
3. K přidání webové služby pro rozhraní použijte nástroj pro konfiguraci modelu služby COM+ (ComSvcConfig. exe). Další informace o použití nástroje ComSvcConfig. exe najdete v tématu [How to: Use a Configuration model Service Model com+](how-to-use-the-com-service-model-configuration-tool.md).  
  
4. Nakonfigurujte všechna další nastavení služby v konfiguračním souboru aplikace. Další informace o tom, jak nakonfigurovat součást, najdete v tématu [How to: Configure a Settings služby com+](how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Podporovaná rozhraní  
 Existují určitá omezení typu rozhraní, která je možné zveřejnit jako webovou službu. Následující typy rozhraní nejsou podporovány:  
  
- Rozhraní, která přecházejí odkazy na objekty jako parametry – následující omezený přístup k objektům je popsán v části Podpora omezeného počtu objektů.  
  
- Rozhraní, která předává typy, které nejsou kompatibilní s konverzemi interoperability .NET Framework COM.  
  
- Rozhraní pro aplikace, které mají povolený fond aplikací, když hostuje model COM+.  
  
- Rozhraní komponent, která jsou pro aplikaci označena jako soukromá.  
  
- Rozhraní infrastruktury COM+.  
  
- Rozhraní ze systémové aplikace.  
  
- Rozhraní z komponent služeb Enterprise Services, které nebyly přidány do globální mezipaměti sestavení (GAC).  
  
### <a name="limited-object-reference-support"></a>Omezená podpora odkazů na objekty  
 Vzhledem k tomu, že řada nasazených komponent modelu COM+ používá objekty podle referenčních parametrů, jako je například vrácení objektu ADO Recordset, integrace modelu COM+ zahrnuje omezené podpory pro parametry odkazů na objekty. Podpora je omezená na objekty, které implementují `IPersistStream` rozhraní com. To zahrnuje objekty ADO sady záznamů a lze je implementovat pro objekty modelu COM specifické pro danou aplikaci.  
  
 Chcete-li povolit tuto podporu, nástroj ComSvcConfig. exe poskytuje přepínač **allowreferences** , který zakáže parametr signatury regulární metody a kontroluje, zda je nástroj spuštěn, aby bylo zajištěno, že parametry objektu reference nejsou používány. Kromě toho musí být typy objektů, které předáváte jako parametry, pojmenovány a identifikovány v rámci `persistableTypes` elementu <> konfigurace, který je podřízenou položkou `comContract` prvku <>.  
  
 Při použití této funkce služba Integration Service modelu COM+ používá `IPersistStream` rozhraní k serializaci nebo deserializaci instance objektu. Pokud instance objektu nepodporuje `IPersistStream` , je vyvolána výjimka.  
  
 V rámci klientské aplikace <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> lze metody objektu použít k předání objektu do služby a podobně k načtení objektu.  
  
> [!NOTE]
> Z důvodu vlastní povahy a specifického přístupu k serializaci je to nejvhodnější pro použití mezi klienty WCF a službami WCF.  
  
## <a name="selecting-the-hosting-mode"></a>Výběr režimu hostování  
 Model COM+ zveřejňuje webové služby v jednom z následujících způsobů hostování:  
  
- COM+ – hostované  
  
     Webová služba je hostována v rámci procesu vyhrazeného serveru COM+ aplikace (Dllhost. exe). Tento režim vyžaduje, aby aplikace byla explicitně spuštěna předtím, než může přijímat žádosti webové služby. Možnosti modelu COM+ "spustit jako službu NT" nebo "ponechat spuštěné v případě nečinnosti" lze použít k zabránění nečinnému vypnutí aplikace a jejích služeb. Tento režim poskytuje obě webové služby i DCOM přístup k serverové aplikaci.  
  
- Hostovaný na webu  
  
     Webová služba je hostována v rámci pracovního procesu webového serveru. Tento režim nevyžaduje, aby model COM+ byl aktivní při přijetí počáteční žádosti. Pokud aplikace není při přijetí této žádosti aktivní, je před zpracováním žádosti automaticky aktivována. Tento režim také poskytuje přístup k serverové aplikaci prostřednictvím webové služby i modelu DCOM, ale vyvolá přesměrování procesu pro žádosti webové služby. To obvykle vyžaduje, aby klient povolil zosobnění. V rámci WCF to lze provést s <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastností <xref:System.ServiceModel.Security.WindowsClientCredential> třídy, která je k dispozici jako vlastnost obecné <xref:System.ServiceModel.ChannelFactory%601> třídy a také jako <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> hodnota výčtu.  
  
- Webový Host v procesu  
  
     Webová služba a logika aplikace modelu COM+ jsou hostovány v rámci pracovního procesu webového serveru. To zajišťuje automatickou aktivaci režimu hostovaného na webu, aniž by to způsobilo přesměrování procesu na požadavky webové služby. Nevýhodou je, že k serverové aplikaci nelze přistup prostřednictvím modelu DCOM.  
  
### <a name="security-considerations"></a>Aspekty zabezpečení  
 Stejně jako jiné služby WCF se nastavení zabezpečení pro vystavené služby spravují prostřednictvím nastavení konfigurace pro kanál WCF. Nejsou vynutila tradiční nastavení zabezpečení DCOM, jako je nastavení oprávnění na úrovni modelu DCOM. Aby bylo možné vyhovět aplikačním rolím COM+, musí být pro danou součást povolena autorizace "kontroly přístupu na úrovni součásti".  
  
 Použití nezabezpečené vazby může opustit komunikaci, která je otevřená pro manipulaci nebo zpřístupnění informací. Abyste tomu předešli, doporučuje se používat zabezpečenou vazbu.  
  
 Pro režimy hostované v modelu COM+ a na webu musí klientské aplikace povolit zosobnění uživatele klienta v procesu serveru. To lze provést v klientech WCF nastavením úrovně zosobnění na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .  
  
 Pomocí služby Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS) pomocí přenosového protokolu HTTP lze použít nástroj Httpcfg. exe k rezervaci adresy koncového bodu přenosu. V jiných konfiguracích je důležité chránit před neautorizovanými službami, které fungují jako zamýšlená služba. Chcete-li zabránit tomu, aby se nepovolená služba spouštěla v požadovaném koncovém bodě, může být legitimní služba nakonfigurována tak, aby běžela jako služba NT. To umožňuje legitimní službě deklarovat adresu koncového bodu před všemi neautorizovanými službami.  
  
 Při vystavení aplikace modelu COM+ s nakonfigurovanými rolemi modelu COM+ jako webové služby, je nutné přidat účet procesu spuštění služby IIS do jedné z rolí aplikace. Tento účet, obvykle s názvem IWAM_machinename, musí být přidán za účelem povolení čistého vypnutí objektů po použití. Účtu by se neměla udělit žádná další oprávnění.  
  
 Funkce recyklace procesu COM+ se nedají použít u integrovaných aplikací. Pokud je aplikace nakonfigurována pro použití recyklace procesu a součásti jsou spuštěny v hostovaném procesu modelu COM+, spuštění služby se nezdařilo. Tento požadavek nezahrnuje služby, které používají režim v rámci hostování na webu, protože nastavení recyklace procesu se nepoužívají.  
  
## <a name="see-also"></a>Viz také

- [Přehled integrace s aplikacemi modelu COM](integrating-with-com-applications-overview.md)
