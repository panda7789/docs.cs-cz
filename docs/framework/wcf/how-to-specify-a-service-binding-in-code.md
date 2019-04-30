---
title: 'Postupy: Určení vazby služby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 9f3320b031141246a394191a1924509204707dc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928801"
---
# <a name="how-to-specify-a-service-binding-in-code"></a>Postupy: Určení vazby služby v kódu
V tomto příkladu `ICalculator` smlouvy je definován pro službu kalkulačky, služba se implementuje v `CalculatorService` třídě a následně svůj koncový bod je definováno v kódu, kde je zadán, že musíte použít službu <xref:System.ServiceModel.BasicHttpBinding> třídy.  
  
 Obvykle je osvědčeným postupem určete vazbu a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby. Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.  
  
 Popis, jak nakonfigurovat tuto službu, pomocí elementů konfigurace namísto kódu najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a>Pokud chcete zadat do kódu pro použití BasicHttpBinding pro službu  
  
1. Definování kontraktu služby pro typ služby.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. Implementace kontraktu služby ve třídě služby.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. V hostitelské aplikace vytvořte základní adresa služby a vazby pro použití se službou.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Vytvoření hostitele pro službu, přidat koncový bod a poté otevřete hostitele.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Chcete-li změnit výchozí hodnoty vlastností vazby  
  
1. Chcete-li změnit jeden z výchozí hodnoty vlastností <xref:System.ServiceModel.BasicHttpBinding> třídy, nastavte hodnotu vlastností pro vazbu na novou hodnotu před vytvořením hostitele. Například pokud chcete změnit výchozí časový limit otevření a zavření hodnoty 1 minuta 2 minuty, použijte následující.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
