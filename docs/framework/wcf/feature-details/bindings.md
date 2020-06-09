---
title: Vazby WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: fd6b942dcabad07feda81af63bde23d3b663ce0f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587609"
---
# <a name="windows-communication-foundation-bindings"></a>Vazby WCF
Windows Communication Foundation (WCF) odděluje způsob, jakým software aplikace zapisuje informace o tom, jak komunikuje s jiným softwarem. Vazby slouží k určení přenosu, kódování a podrobností protokolu požadovaných pro komunikaci mezi klienty a službami. WCF používá vazby k vygenerování podkladové reprezentace koncového bodu, takže většina podrobností o vazbě musí být odsouhlasena stranami, které komunikuje. Nejjednodušší způsob, jak toho dosáhnout, je, aby klienti služby používali stejnou vazbu, kterou používá koncový bod pro službu. Další informace o tom, jak to provést, najdete v tématu [použití vazeb ke konfiguraci služeb a klientů](../using-bindings-to-configure-services-and-clients.md).  
  
 Vazba se skládá z kolekce elementů vazby. Každý prvek popisuje nějaký aspekt toho, jak koncový bod komunikuje s klienty. Vazba musí obsahovat alespoň jeden element transportních vazeb, alespoň jeden element vazby v kódování zprávy (který může ve výchozím nastavení poskytnout element vazby přenosu) a libovolný počet dalších prvků vazby protokolu. Proces, který vytváří modul runtime z tohoto popisu, umožňuje každému elementu vazby přispívat kód do tohoto modulu runtime.  
  
 WCF poskytuje vazby, které obsahují běžné výběry prvků vazby. Je možné je použít s jejich výchozími nastaveními nebo můžete tyto výchozí hodnoty upravit podle požadavků uživatelů. Tyto vazby poskytnuté systémem mají vlastnosti, které umožňují přímou kontrolu nad prvky vazby a jejich nastavením. Můžete také snadno pracovat s více verzemi vazby tím, že všem verzím vazby udělíte vlastní název. Podrobnosti najdete v tématu [Konfigurace vazeb poskytovaných systémem](configuring-system-provided-bindings.md).  
  
 Pokud potřebujete kolekci prvků vazby, které nejsou poskytovány některou z těchto vazeb poskytovaných systémem, můžete vytvořit vlastní vazbu, která se skládá z kolekce elementů vazby, které jsou požadovány. Tyto vlastní vazby je snadné vytvořit a nevyžadují novou třídu, ale neposkytují vlastnosti pro řízení prvků vazby nebo jejich nastavení. K prvkům vazby můžete přistupovat a upravit jejich nastavení pomocí kolekce, která je obsahuje. Podrobnosti najdete v tématu [vlastní vazby](../extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Konfigurace vazeb poskytovaných systémem](configuring-system-provided-bindings.md)  
 Popisuje, jak používat a upravovat vazby, které WCF poskytuje pro podporu běžných scénářů.  
  
 [Používání vazeb ke konfiguraci služeb a klientů](../using-bindings-to-configure-services-and-clients.md)  
 Popisuje definování vazeb Windows Communication Foundation (WCF) pro služby a klienty imperativně v kódu a deklarativní použití konfigurace.  
  
 [Vlastní vazby](../extending/custom-bindings.md)  
 Popisuje, co <xref:System.ServiceModel.Channels.CustomBinding> je a kdy se používá.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšíření vazeb](../extending/extending-bindings.md)
