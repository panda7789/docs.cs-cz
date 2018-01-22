---
title: Vazby WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 494869985f14dc9562b8d98a7d68cd9639cca97b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="windows-communcation-foundation-bindings"></a>Vazby WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]odděluje postup zápisu softwaru pro aplikaci z jak komunikuje s jiným softwarem. Vazby slouží k určení přenosu, kódování a podrobnosti protokolu povinné pro klienty a služby pro komunikaci mezi sebou. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]vazby se používá ke generování základní síťové vyjádření koncového bodu, takže většina podrobnosti vazba musí schválit strany, které komunikují. Nejjednodušší způsob, jak dosáhnout je pro klientům služby používat stejnou vazbu, která koncový bod služby používá. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak to udělat, najdete v části [pomocí vazby na klienty a konfiguraci služby Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Vazba se skládá z kolekce elementů vazby. Každý prvek popisuje určitý aspekt jak koncový bod komunikuje s klienty. Vazba musí obsahovat alespoň jeden element vazby přenosu, alespoň jeden kódování zpráv prvku vazby (což element vazby přenosu může zajistit ve výchozím nastavení) a libovolný počet dalších protokol prvky vazeb. Proces, který sestaví runtime mimo tento popis umožňuje každého prvku vazby přispívání kód pro tento modul runtime.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje vazby, které obsahují běžné možnosti elementů vazby. Ty mohou být použity ve výchozím nastavení, nebo můžete upravit tyto výchozí hodnoty podle požadavků uživatelů. Tyto vazby poskytované systémem mít vlastnosti, které umožňují přímou kontrolu nad prvky vazby a jejich nastavení. Můžete také snadno pracovat souběžného s více verzemi vazby tím, že každou verzi vazby svůj vlastní název. Podrobnosti najdete v tématu [Configuring System-Provided vazby](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Pokud potřebujete kolekce elementů vazby není poskytovaný jednu z těchto vazeb poskytovaných systémem můžete vytvořit vlastní vazby, která se skládá z kolekce elementů požadované vazby. Tyto vlastních vazeb se dají snadno vytvářet a provádět nevyžadují novou třídu, ale není zadejte vlastnosti pro řízení prvky vazby nebo jejich nastavení. Můžete používat prvky vazby a změnit jejich nastavení prostřednictvím kolekce, která obsahuje je. Podrobnosti najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Konfigurace vazeb poskytovaných systémem](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Popisuje, jak používat a upravovat vazby, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje pro podporu běžné scénáře.  
  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Popisuje, jak definovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vazeb pro služby a klienti imperativní v kódu a deklarativně pomocí konfigurace.  
  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Popisuje, co <xref:System.ServiceModel.Channels.CustomBinding> je a pokud se používá.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)
