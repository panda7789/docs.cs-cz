---
title: 'Postupy: Zadání vazby služby v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 3c6cfd084055d59d3292b49897ff710f14f92737
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320876"
---
# <a name="how-to-specify-a-service-binding-in-code"></a>Postupy: Zadání vazby služby v kódu
V tomto příkladu je pro službu kalkulačky definována smlouva `ICalculator`, služba je implementována ve třídě `CalculatorService` a poté je její koncový bod definován v kódu, kde je určeno, že služba musí používat třídu <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Obvykle je osvědčeným postupem zadat vazby a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby. Obecně platí, že zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace nebo opětovného nasazení aplikace.  
  
 Popis postupu konfigurace této služby pomocí prvků konfigurace namísto kódu naleznete v tématu [How to: zadat vazbu služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md).  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a>Zadání v kódu pro použití BasicHttpBinding pro službu  
  
1. Definujte kontrakt služby pro typ služby.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. Implementujte kontrakt služby ve třídě služby.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. V hostitelské aplikaci vytvořte základní adresu pro službu a vazbu, která se má používat se službou.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Vytvořte hostitele pro službu, přidejte koncový bod a pak otevřete hostitele.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Úprava výchozích hodnot vlastností vazby  
  
1. Chcete-li upravit jednu z hodnot výchozí vlastnosti třídy <xref:System.ServiceModel.BasicHttpBinding>, nastavte hodnotu vlastnosti vazby na novou hodnotu před vytvořením hostitele. Pokud například chcete změnit výchozí hodnoty časového limitu pro otevření a zavření 1 minuty na 2 minuty, použijte následující.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
- [Zadání adresy koncového bodu](specifying-an-endpoint-address.md)
