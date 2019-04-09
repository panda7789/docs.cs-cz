---
title: Vlastní upgrady streamů
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: cd8385194e1f24d246e6fc398462b45bacbe15d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127358"
---
# <a name="custom-stream-upgrades"></a>Vlastní upgrady streamů
Orientovaný na Stream přenosy, jako je například TCP a pojmenované kanály pracovat nepřetržitý datový proud bajtů mezi klientem a serverem. Tento datový proud se provádí <xref:System.IO.Stream> objektu. Při upgradu datového proudu klient chce přidat volitelné protokolové vrstvě kanálu zásobníku a zeptá druhém konci komunikační kanál k tomu. Se skládá z upgradu datového proudu nahrazení původní <xref:System.IO.Stream> objekt upgradovaný sadou.  
  
 Můžete například vytvořit kompresního datového proudu přímo přes přenosový stream. V tomto případě původní přenosu <xref:System.IO.Stream> nahradí jednu, která obaluje komprese <xref:System.IO.Stream> kolem původní.  
  
 Můžete použít více upgrady streamů, každý obtékání ta předchozí.  
  
## <a name="how-stream-upgrades-work"></a>Jak inovace Stream  
 Existují čtyři součásti procesu upgradu datového proudu.  
  
1.  Upgrade datového proudu *iniciátoru* zahájí proces: v době běhu ho můžete iniciovat požadavek na druhém konci připojení upgrade přenosové vrstvě kanálu.  
  
2.  Upgrade datového proudu *dodavatel* provádí upgrade: v době běhu obdrží požadavek na upgrade z druhého počítače a pokud je to možné, přijímá inovace.  
  
3.  Upgrade *poskytovatele* vytvoří *iniciátoru* na straně klienta a *dodavatel* na serveru.  
  
4.  Upgrade datového proudu *prvku vazby* se přidá do vazby na službu a klienta a vytvoří poskytovatel za běhu.  
  
 Všimněte si, že v případě více upgradů, iniciátora a příjemce zapouzdření stavu počítače k vynucení, které upgradu přechody jsou platné pro každé spuštění.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Jak implementovat Stream upgradu  
 Windows Communication Foundation (WCF) poskytuje čtyři `abstract` třídy, které můžete implementovat:  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 K provedení upgradu na vlastní datový proud, postupujte takto. Tento postup implementuje procesu upgradu minimální datového proudu na počítačích klienta i serveru.  
  
1.  Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1.  Přepsat <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> metoda do datového proudu k upgradovány a vrátí upgradovaný datového proudu. Tato metoda pracuje synchronně, hodnota jsou obdobou metody k zahájení upgradu asynchronně.  
  
    2.  Přepsat <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metodu ke kontrole pro další upgrady.  
  
2.  Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1.  Přepsat <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> metoda do datového proudu k upgradovány a vrátí upgradovaný datového proudu. Tato metoda pracuje synchronně, hodnota Potvrďte upgrade asynchronně obdobná způsoby.  
  
    2.  Přepsat <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metodou ke zjištění, pokud požadovaný upgrade podporuje tento upgrade příjemce v tuto chvíli v procesu upgradu.  
  
3.  Vytvořte třídu implementuje <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Přepsat <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> a <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> metody vrátí instance dodavatel a iniciátor definovaný v kroku 2 a 1.  
  
4.  Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1.  Přepsat <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> metody na straně klienta a <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> metodu na službu.  
  
    2.  Přepsat <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> metody na straně klienta a <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> metodu na službu přidat Element upgradu vazby na <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5.  Přidáte nový element vazby upgradu datového proudu do vazby na serverových a klientských počítačích.  
  
## <a name="security-upgrades"></a>Upgradů zabezpečení  
 Přidání upgrade zabezpečení je specializované verze procesu upgradu obecné datového proudu.  
  
 WCF již obsahuje dva prvky vazeb pro upgrade zabezpečení proudu. Konfigurace zabezpečení transportní vrstvy jsou zapouzdřena objektem <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> a <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> která můžete nakonfigurovat a přidat do vlastní vazby. Tyto prvky vazeb rozšířit <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> třídu, která vytvoří datový proud klientských a serverových upgradu poskytovatelů. Tyto prvky vazby mít metody, které vytvořit datový proud zabezpečení specializované třídy upgradu zprostředkovatele, které nejsou `public`, takže za jednotlivé způsoby všechno, co potřebujete udělat je přidat element vazby do vazby.  
  
 Pro scénáře zabezpečení nebyly splněny podle výše uvedených elementů vazby dvě, tři související se zabezpečením `abstract` jsou třídy odvozeny z výše uvedených iniciátor, dodavatel a zprostředkovatele základních tříd:  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Proces implementace upgrade zabezpečení proudu je stejná jako předtím, s tím rozdílem, že by jsou odvozeny z těchto tří tříd. Přepište další vlastnosti v těchto třídách slouží k poskytování informací o zabezpečení modulu runtime.  
  
## <a name="multiple-upgrades"></a>Více upgradů  
 Chcete-li vytvořit další požadavky na upgrade postupujte stejně jako výše: vytvořit další rozšíření <xref:System.ServiceModel.Channels.StreamUpgradeProvider> a elementů vazby. Přidání elementů vazby do vazby. Prvky další vazby se provádějí postupně, počínaje prvním prvkem vazby přidá do vazby. V <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> a <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> každý upgradu poskytovatel může zjistit, jak sám vrstvy na jakékoli existující upgrade vazby parametrů. Pak by mělo nahradit stávající upgrade vazby parametru se nový parametr vazbu složený upgradu.  
  
 Alternativně jednoho poskytovatele upgradu může podporovat více upgradů. Například můžete implementovat vlastní datový proud upgradu poskytovatele, který podporuje zabezpečení a komprese. Proveďte následující kroky:  
  
1.  Podtřídy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> zapisovat zprostředkovatele třídu, která vytvoří iniciátoru a příjemce.  
  
2.  Podtřídy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> nezapomeňte přepsat <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metoda vrátí typy obsahu pro kompresního datového proudu a zabezpečené datového proudu v pořadí.  
  
3.  Podtřídy <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> , které rozumí vlastní typy obsahu v jeho <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metoda.  
  
4.  Datový proud se upgraduje za každé volání <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> a <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
