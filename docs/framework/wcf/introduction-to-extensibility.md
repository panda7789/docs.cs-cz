---
title: Úvod do rozšíření
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: ae820e88a790aeaad7c57cde2db84b8168f273a9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321056"
---
# <a name="introduction-to-extensibility"></a>Úvod do rozšíření
Model aplikace Windows Communication Foundation (WCF) je navržený tak, aby vyřešil větší část požadavků na komunikaci jakékoli distribuované aplikace. Existují však vždy scénáře, že výchozí model aplikace a implementace systému nejsou podporovány. Model rozšiřitelnosti WCF je určený k podpoře vlastních scénářů tím, že vám umožní změnit chování systému na všech úrovních, a to i v případě, že se nahradí celý model aplikace. Toto téma popisuje různé oblasti rozšíření a odkazuje na Další informace o každé z nich.  
  
## <a name="areas-to-extend"></a>Oblasti, které se mají zvětšit  
 Můžete roztáhnout:  
  
- Modul runtime aplikace Tím se rozšíří odesílání a zpracování zpráv pro aplikaci. Tato oblast také obsahuje rozšíření systému zabezpečení, systému metadat, systému serializace a vazeb a elementů vazby, které připojují aplikaci k základnímu systému kanálů.  
  
- Modul runtime kanálu a kanálu. Tím se rozšíří systém, který funguje na úrovni zprávy, poskytuje podporu protokolů, přenosů a kódování.  
  
- Modul runtime hostitele. Tím se rozšiřuje vztah domény hostující aplikace na modul runtime kanálu a aplikace.  
  
### <a name="extending-the-application-runtime"></a>Rozšíření modulu runtime aplikace  
 V aplikacích WCF existuje rozdíl mezi zprávami, které jsou určeny pro odpovídající kanál a zprávy určené pro samotnou aplikaci. Zprávy kanálu podporují některé funkce související s kanálem, jako je třeba vytvoření zabezpečené konverzace nebo vytvoření spolehlivé relace. Tyto zprávy nejsou k dispozici pro modul runtime aplikace. jsou zpracovávány před tím, než je zahrnuta aplikační vrstva.  
  
 Zprávy aplikací obsahují data určená pro operaci klienta nebo služby, kterou jste vy nebo váš zákazník vytvořili. Tyto zprávy jsou k dispozici pro systém rozšíření na úrovni aplikace ve formě zprávy nebo objektu v závislosti na vašich potřebách.  
  
 Všechny zprávy procházejí systémem kanálu; ze systému kanálu do aplikace jsou předávány pouze zprávy aplikace. Chcete-li vytvořit nové funkce na úrovni kanálu, je nutné, abyste rozšířili systém kanálu. Chcete-li vytvořit nové funkce na úrovni aplikace, je nutné, abyste rozšířili službu nebo modul runtime klienta (odeslané moduly a továrny kanálů). Další informace o rozšíření modulu runtime aplikace naleznete v tématu [Rozšíření ServiceHost a vrstva modelu služby](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Rozšíření zabezpečení  
 Chcete-li vytvořit vlastní mechanismy zabezpečení, jako jsou tokeny a přihlašovací údaje, je nutné, abyste rozšířili systém zabezpečení. Další informace najdete v tématu [rozšíření zabezpečení](./extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Rozšíření metadat  
 Chcete-li svá metadata vystavit jinak než ve výchozím nastavení, je nutné systém metadat zvětšit. Další informace najdete v tématu [rozšíření systému metadat](./extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Rozšíření serializace  
 Chcete-li vytvořit vlastní kodéry, poskytnout náhradní data nebo jinou práci zahrnující přizpůsobení přenesených dat, je nutné systém serializace zvětšit. Další informace najdete v tématu [rozšíření kodérů a serializátorů](./extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Rozšiřování vazeb  
 Chcete-li přidružit kanály přenosu nebo protokolu k aplikační vrstvě, je nutné zvětšit systém vazby. Další informace najdete v tématu [rozšíření vazeb](./extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Rozšíření systému kanálu  
 Pokud chcete vytvořit kanály, které podporují vlastní přenosy nebo funkce protokolu, přečtěte si téma [rozšíření vrstvy kanálu](./extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Rozšíření hostitelského systému služby  
 Chcete-li upravit aplikační model pro všechny služby, je nutné, abyste rozšířili třídu <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Další informace najdete v tématu [Rozšíření ServiceHost a vrstva modelu služby](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Chcete-li upravit vztah mezi doménou hostující aplikace a hostitelem služby, je nutné zvětšit třídu <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType>. Další informace najdete v tématu [rozšíření hostování pomocí ServiceHostFactory](./extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření WCF](./extending/index.md)
