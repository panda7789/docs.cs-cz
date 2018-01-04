---
title: "Postupy: Zadání vazby služby v kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a852fddcfa5aadbd5a942929bd131588e652cacb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-a-service-binding-in-code"></a>Postupy: Zadání vazby služby v kódu
V tomto příkladu `ICalculator` kontrakt je definována pro službu kalkulačky, služba se implementuje v `CalculatorService` třídě a následně svůj koncový bod je definována v kódu, kde je zadán, že musí používat službu <xref:System.ServiceModel.BasicHttpBinding> třídy.  
  
 Obvykle je osvědčeným postupem zadejte vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativní v kódu. Definování koncové body v kódu obvykle není praktické protože jsou obvykle liší od těch, které používá při služby je vyvíjen vazeb a adresy pro v nasazené službě. Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu zkompiluje nebo znovu nasadit aplikaci.  
  
 Popis toho, jak nakonfigurovat tuto službu pomocí konfigurace – elementy místo kód, najdete v části [postupy: zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a>Pokud chcete zadat do kódu pro použití BasicHttpBinding pro službu  
  
1.  Definování kontraktu služby pro typ služby.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  Implementujte kontrakt služby v třídě služby.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  V hostitelských aplikaci vytvořte základní adresu pro tuto službu a vazby pro použití se službou.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  Vytvořte hostitele služby, přidat koncový bod a pak otevřete hostitele.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Chcete-li změnit výchozí hodnoty vlastností vazby  
  
1.  K úpravě jeden z výchozí hodnoty vlastností <xref:System.ServiceModel.BasicHttpBinding> třídy, nastavte hodnotu vlastnosti o vazbě na novou hodnotu před vytvořením hostitele. Například změnit výchozí časový limit pro otevření a zavření hodnoty 1 minuta na 2 minuty, použijte následující příkaz.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
