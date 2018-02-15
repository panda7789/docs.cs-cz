---
title: "Úvod do rozšíření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e16ed674c87bdb1418257a30f7f79b970127b06
ms.sourcegitcommit: 08684dd61444c2f072b89b926370f750e456fca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="introduction-to-extensibility"></a>Úvod do rozšíření
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Aplikačního modelu je proto, aby vyřešila větší část požadavky na komunikaci všechny distribuované aplikace. Ale stále existují scénáře, které výchozí aplikačního modelu a implementace poskytované systémem nepodporují. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Model rozšiřitelnosti je určená pro podporu vlastní scénáře tím, že umožňuje, abyste upravili chování systému na všech úrovních, a to i do bodu nahrazení modelu celou aplikaci. Toto téma popisuje různé oblasti rozšíření a odkazuje na další informace o jednotlivých.  
  
## <a name="areas-to-extend"></a>Oblasti, které rozšiřují  
 Můžete rozšířit:  
  
-   Doba spuštění aplikace. Tato zásada rozšiřuje odeslání a zpracování zpráv pro aplikaci. Tato oblast zahrnuje taky rozšíření systému zabezpečení, systém metadat, systém serializace a vazby a elementů, které se připojují aplikace s podkladový systém kanál vazby.  
  
-   Kanál a kanál runtime. Tato zásada rozšiřuje systém, který funguje na úrovni zpráv, poskytuje protokol, přenos a kódování podpory.  
  
-   Modul runtime hostitele. Tato zásada rozšiřuje vztah hostování domény aplikace do runtime kanál a aplikace.  
  
### <a name="extending-the-application-runtime"></a>Rozšíření doba spuštění aplikace  
 V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace, je rozdíl mezi zprávy, které jsou určené pro odpovídající kanál a zprávy, které jsou určené pro vlastní aplikace. Kanál zprávy podporovat některé funkce související s kanál, například vytvoření zabezpečenou konverzaci nebo vytvoření spolehlivé relace. Tyto zprávy nejsou k dispozici pro doba spuštění aplikace; jsou zpracovávány předtím, než je zahrnuta aplikační vrstvu.  
  
 Zprávy aplikace obsahovat data, která je určena pro klienta nebo operace služby, který jste nebo zákazníkovi vytvořil. Tyto zprávy jsou k dispozici pro systém rozšíření na úrovni aplikací v podobě zprávy nebo objekt, v závislosti na vašich potřeb.  
  
 Všechny zprávy předat prostřednictvím kanálu systému; pouze zprávy aplikace jsou předávány ze systému kanálu do aplikace. Chcete-li vytvořit nové funkce na úrovni kanálů, musíte rozšířit systému kanál. Pokud chcete vytvořit nové funkce na úrovni aplikace, musíte rozšířit runtime služba nebo klienta (dispečerů a továren kanál v uvedeném pořadí). [!INCLUDE[crabout](../../../includes/crabout-md.md)] rozšíření modulu runtime aplikace, najdete v části [rozšíření ServiceHost a vrstva modelu služby](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Rozšíření zabezpečení  
 Pokud chcete vytvořit vlastní zabezpečovací mechanismy, například tokeny a přihlašovací údaje, musíte rozšířit zabezpečení systému. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Rozšíření zabezpečení](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Rozšíření metadat  
 Metadata v vystavit jinak než výchozí, musíte rozšířit systém metadat. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Rozšíření systému metadat](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Rozšíření serializace  
 Sestavení vlastní kodéry, zadejte data náhrady nebo jiné pracovní zahrnující přizpůsobení přenášených dat, musíte rozšířit systému serializace. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Rozšiřování kodérů a Serializátorů](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Rozšiřování vazeb  
 K přenosu nebo protokol kanálů přidružit aplikační vrstvu, musíte rozšířit vazba systému. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Rozšiřování vazeb](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Rozšíření systému kanálu  
 K vytvoření kanálů, které podporují vlastní přenosy nebo protokolu funkce, najdete v části [rozšíření vrstvy kanálu](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Rozšíření hostování systému  
 Pokud chcete upravit celé služby aplikačního modelu, musíte rozšířit <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> třídy. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Rozšíření ServiceHost a vrstva modelu služby](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Pokud chcete upravit vztah mezi hostování domény aplikace a hostitele služby, musíte rozšířit <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> třídy. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Rozšíření hostování pomocí třídy ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření WCF](../../../docs/framework/wcf/extending/index.md)
