---
title: "Vlastní upgrady streamů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20b061418ee2dc6c3adcde5553d29e680d739582
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-stream-upgrades"></a>Vlastní upgrady streamů
Datový proud orientované přenosy například TCP a pojmenované kanály pracovat nepřetržitý proud bajtů mezi klientem a serverem. Tento datový proud je realizován pomocí <xref:System.IO.Stream> objektu. V případě upgradu datového proudu klient chce, aby se k přidání volitelné protokol vrstvy kanálu zásobníku a požádá druhém konci komunikační kanál Uděláte to tak. Upgrade datového proudu se skládá v nahrazení původní <xref:System.IO.Stream> objekt s některého upgradovaný.  
  
 Můžete například vytvořit kompresního streamu přímo na základě datového proudu přenosu. V tomto případě původní přenos <xref:System.IO.Stream> se nahradí ten, který zabalí komprese <xref:System.IO.Stream> kolem původnímu.  
  
 Můžete použít více upgradů datového proudu, každý zabalení ten předchozí.  
  
## <a name="how-stream-upgrades-work"></a>Jak datového proudu upgraduje pracovní  
 Existují čtyři součásti pro proces upgradu datového proudu.  
  
1.  Upgrade datového proudu *iniciátor* zahájí proces: při spuštění ho můžete zahájit požadavek na druhém konci připojení k upgradu přenosové vrstvy kanálu.  
  
2.  Upgrade datového proudu *dodavatelem* provede upgrade: při spuštění obdrží žádost o upgrade z jiné počítače a pokud je to možné, přijímá upgradu.  
  
3.  Upgrade *zprostředkovatele* vytvoří *iniciátor* na straně klienta a *dodavatelem* na serveru.  
  
4.  Upgrade datového proudu *vazby Element* se přidá do vazby na službu a klienta a vytvoří zprostředkovatele za běhu.  
  
 Všimněte si, že v případě více upgradů iniciátor a dodavatel zapouzdření stavu počítače k vynucení, který upgradu přechody jsou platné pro každé spuštění.  
  
## <a name="how-to-implement-a-stream-upgrade"></a>Jak implementovat upgradu datového proudu  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje čtyři `abstract` třídy, které můžete implementovat:  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 Chcete-li implementovat vlastní datový proud upgrade, postupujte takto. Tento postup implementuje procesu upgradu minimální datový proud na počítačích, klient i server.  
  
1.  Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.  
  
    1.  Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> metoda provést v datovém proudu upgradovat a vrátíte se do upgradovaný datového proudu. Tato metoda funguje synchronně; asynchronně zahájit upgrade podobá způsoby.  
  
    2.  Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metoda zkontrolujte další možnosti upgradu.  
  
2.  Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.  
  
    1.  Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> metoda provést v datovém proudu upgradovat a vrátíte se do upgradovaný datového proudu. Tato metoda funguje synchronně; jsou obdobou metody tak, aby přijímal upgradu asynchronně.  
  
    2.  Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metoda k určení, pokud je upgrade požadovaný nepodporuje tento upgrade dodavatel v tomto okamžiku v procesu upgradu.  
  
3.  Vytvořte třídu implementuje <xref:System.ServiceModel.Channels.StreamUpgradeProvider>. Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> a <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> metody vrátit instance dodavatel a iniciátor definovaný v kroku 2 a 1.  
  
4.  Vytvořte třídu, která implementuje <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.  
  
    1.  Přepsání <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> metody na straně klienta a <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> metoda ve službě.  
  
    2.  Přepsání <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> metody na straně klienta a <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> metoda na službu, kterou chcete přidat upgradu vazby elementu, který chcete <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.  
  
5.  Přidáte nový element upgradu vazby datového proudu do vazby u serverových a klientských počítačů.  
  
## <a name="security-upgrades"></a>Upgrady zabezpečení  
 Přidání upgrade zabezpečení je specializovanou verzi procesu upgradu obecné datového proudu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]již poskytuje dva elementy vazby pro upgrade zabezpečení datového proudu. Konfigurace zabezpečení na úrovni přenosu je zapouzdřené pomocí <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> a <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> které mohou být konfigurovány a přidat do vlastní vazby. Tyto prvky vazeb rozšířit <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> třídu, která vytvoří datový proud klientských a serverových upgradu zprostředkovatele. Tyto prvky vazeb mají metody, které vytvoření datového proudu specializované zabezpečení třídy upgradu zprostředkovatele, které nejsou `public`, takže pro tyto dva případy všechny musíte udělat je přidat do vazby prvku vazby.  
  
 Pro scénáře zabezpečení nejsou splněny ve výše uvedené prvky dvě vazby, tři související se zabezpečením `abstract` třídy jsou odvozené z výše uvedených iniciátor, dodavatel a zprostředkovatele základních tříd:  
  
1.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3.  <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 Proces implementace upgrade datového proudu zabezpečení je stejná jako předtím, s tím rozdílem, že by odvozena z těchto tří tříd. Přepsání dalších vlastností v těchto tříd zadat informace o zabezpečení modulu runtime.  
  
## <a name="multiple-upgrades"></a>Více upgradů  
 Vytvořit další upgradu požadavky, opakujte výše postup: vytvoření další rozšíření <xref:System.ServiceModel.Channels.StreamUpgradeProvider> a elementů vazby. Prvky vazby přidáte vazbu. Prvky další vazby jsou zpracovávány postupně, počínaje první vazba prvek přidán do vazby. V <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> a <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> každý poskytovatel upgradu můžete určit, jak se sám vrstvy na všechny existující upgrade vazby parametrů. Potom by mělo nahradit existující upgradu vazba parametru s nový parametr složené upgradu vazbu.  
  
 Alternativně jednoho poskytovatele upgradu může podporovat více upgradů. Například můžete chtít implementovat vlastní datový proud upgradu zprostředkovatele, který podporuje zabezpečení a komprese. Proveďte následující kroky:  
  
1.  Podtřída <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> zapisovat zprostředkovatele třídu, která vytvoří iniciátor a příjemce.  
  
2.  Podtřída <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> a zkontrolujte, zda přepsat <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> metoda vrátí typy obsahu pro kompresního streamu a zabezpečený datový proud v pořadí.  
  
3.  Podtřída <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> , rozumí vlastní typy obsahu v jeho <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> metoda.  
  
4.  Datový proud se upgraduje po každé volání <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> a <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>  
 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>  
 <xref:System.ServiceModel.Channels.StreamUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>  
 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
