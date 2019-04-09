---
title: Úvod do rozšíření
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: 8d7b9c811c557b10160c2581a59f5ebf72882bfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147040"
---
# <a name="introduction-to-extensibility"></a>Úvod do rozšíření
Model aplikace Windows Communication Foundation (WCF) je navržená k řešení větší část požadavky na komunikaci všechny distribuované aplikace. Ale vždy existují scénáře, které výchozí aplikační model a implementace poskytované systémem nepodporují. Model rozšiřitelnosti WCF je určený pro podporu vlastní scénáře tím, že abyste upravili chování systému na všech úrovních, dokonce i do bodu nahrazení modelu celé aplikace. Toto téma popisuje různé oblasti rozšíření a odkazuje na další informace o jednotlivých.  
  
## <a name="areas-to-extend"></a>Rozšíření oblastí  
 Můžete rozšířit:  
  
-   Doba spuštění aplikace. Tato zásada rozšiřuje, odesílání a zpracování zpráv pro aplikaci. Tato oblast také obsahuje rozšíření systému zabezpečení, systému metadat, systém serializace a vazby a prvky, které k základní kanál systému připojit aplikace vazbu.  
  
-   Kanál a modulu runtime kanálu. Tato zásada rozšiřuje na systém, který funguje na úrovni zprávy, nabízí protokol, přenosu a podpory kódování.  
  
-   Modul runtime hostitele. Tato zásada rozšiřuje vztah hostování aplikační domény na modul runtime kanálu a aplikace.  
  
### <a name="extending-the-application-runtime"></a>Rozšíření modulu Runtime aplikace  
 Aplikace WCF je rozdíl mezi zprávy, které jsou určeny pro odpovídající kanál a zprávy, které jsou určeny pro vlastní aplikace. Zprávy kanálu podporovat některé funkce související s kanál, třeba navázání zabezpečené konverzace nebo vytvoření stabilní relace. Tyto zprávy nejsou k dispozici pro spuštění aplikace; jsou zpracovávány předtím, než je zahrnuta aplikační vrstvu.  
  
 Aplikace zprávy obsahují data, která je určena pro klienta nebo operace služby, které vy nebo váš zákazník vytvořil. Tyto zprávy jsou k dispozici systému rozšíření na úrovni aplikace ve zprávě nebo Objektové formě, v závislosti na vašich potřeb.  
  
 Všechny zprávy předat prostřednictvím kanálu systému; pouze zprávy aplikace se předávají ze systému kanál do aplikace. Pokud chcete vytvořit nové funkce na úrovni kanálu, musíte rozšířit kanál systému. Pokud chcete vytvořit nové funkce na úrovni aplikace, je třeba rozšířit modul runtime služby ani klienta (dispečerů a objekty pro vytváření kanálů, v uvedeném pořadí). Další informace o rozšíření modulu runtime aplikace najdete v tématu [rozšíření ServiceHost a vrstva modelu služby](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Rozšíření zabezpečení  
 Pokud chcete vytvořit vlastní bezpečnostní mechanismy, jako je tokeny a přihlašovací údaje, je třeba rozšířit systém zabezpečení. Další informace najdete v tématu [rozšíření zabezpečení](../../../docs/framework/wcf/extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Rozšíření metadat  
 Pokud chcete zpřístupnit vaše metadata v jinak než výchozí, musí rozšíření systému metadat. Další informace najdete v tématu [rozšíření systému metadat](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Rozšíření serializace  
 Vytvářet vlastní kodéry, zadejte náhrady dat nebo jiné pracovní zahrnující přizpůsobení přenášená data, je třeba rozšířit systém serializace. Další informace najdete v tématu [rozšiřování kodérů a Serializátorů](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Rozšiřování vazeb  
 Pokud chcete přidružit k přenosu nebo protokol kanály aplikační vrstvu, je třeba rozšířit systém vazby. Další informace najdete v tématu [rozšíření vazby](../../../docs/framework/wcf/extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Rozšíření systému kanálu  
 Vytvoření kanálů, které podporují vlastní přenosy nebo protokol funkce najdete v tématu [rozšíření vrstvy kanálu](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Rozšíření hostování systému  
 Chcete-li změnit model služby aplikace, je třeba rozšířit <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> třídy. Další informace najdete v tématu [rozšíření ServiceHost a vrstva modelu služby](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Pokud chcete upravit vztah hostování domény aplikace a hostitel služby, je třeba rozšířit <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> třídy. Další informace najdete v tématu [rozšíření hostování pomocí ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření WCF](../../../docs/framework/wcf/extending/index.md)
