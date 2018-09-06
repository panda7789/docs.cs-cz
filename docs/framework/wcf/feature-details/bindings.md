---
title: Vazby WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 1930826cf51d67ceb789e20920ca42f04d1adc1b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734353"
---
# <a name="windows-communication-foundation-bindings"></a>Vazby WCF
Windows Communication Foundation (WCF) odděluje, jak software pro aplikaci vypíše jak komunikuje s jiným softwarem. Vazby se používají k určení přenosu, kódování a podrobnosti protokolu pro klienty a služby musí komunikovat mezi sebou. Vazby WCF používá ke generování podkladové síťové vyjádření koncového bodu, takže většina podrobnosti vazby musí schválit stranami, které komunikují. Nejjednodušší způsob, jak toho dosáhnout, je pro klienty služby použít stejné vazby, který koncový bod pro použití služby. Další informace o tom, jak to provést, najdete v části [vazby pomocí konfigurace služby Windows Communication Foundation a klientům](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Vazba se skládá z kolekce elementů vazby. Každý prvek popisuje určitý aspekt jak koncový bod komunikuje s klienty. Vazby musí obsahovat alespoň jeden element vazby přenosu, aspoň jeden kódování zpráv element vazby (které ve výchozím nastavení můžou poskytovat element vazby přenosu) a prvky vazeb protokolu libovolný počet dalších. Proces, který modul runtime mimo tento popis umožňuje každé vazby přispívat kód do tohoto modulu runtime.  
  
 WCF poskytuje vazby, které obsahují běžné možnosti elementů vazby. Ty je možné použít ve výchozím nastavení, nebo můžete upravit tyto výchozí hodnoty podle požadavků uživatele. Tyto vazby poskytované systémem mají vlastnosti, které umožňují přímou kontrolu nad prvky vazby a jejich nastavení. Můžete také snadno pracovat – souběžně s více verzemi vazbu tím, že každá verze vazby svůj vlastní název. Podrobnosti najdete v tématu [Configuring System-Provided vazby](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Pokud budete potřebovat kolekci elementů vazby není zadaný pomocí jedné z těchto vazeb poskytovaných systémem, můžete vytvořit vlastní vazby, který se skládá z kolekce elementů požadované vazby. Tyto vlastní vazby se dají snadno vytvořit a proveďte novou třídu, aby, ale neposkytují vlastností pro řízení elementů vazby nebo jejich nastavení. Můžete přistupovat k prvkům vazby a upravit jejich nastavení prostřednictvím kolekce, která je obsahuje. Podrobnosti najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Konfigurace vazeb poskytovaných systémem](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Popisuje, jak používat a upravovat vazby, které poskytuje WCF k podpoře běžných scénářů.  
  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Popisuje, jak definovat vazby Windows Communication Foundation (WCF) pro služby a klienti imperativně v kódu a deklarativně pomocí konfigurace.  
  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Popisuje, co <xref:System.ServiceModel.Channels.CustomBinding> je a pokud je použit.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)
