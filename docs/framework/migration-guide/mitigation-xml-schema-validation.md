---
title: 'Omezení rizik: Ověření schématu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc0232e0187c795fe20e6a99d4a710ba6244e34e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599663"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="231b1-102">Omezení rizik: Ověření schématu XML</span><span class="sxs-lookup"><span data-stu-id="231b1-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="231b1-103">V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], ověření schématu XSD rozpozná porušení omezení unique, pokud se používá složený klíč a jeden klíč je prázdný.</span><span class="sxs-lookup"><span data-stu-id="231b1-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="231b1-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="231b1-104">Impact</span></span>  
 <span data-ttu-id="231b1-105">Dopad této změny by měl být minimální: podle specifikace schématu, Chyba ověření schématu se očekává, pokud `xsd:unique` porušení pomocí složeného klíče s prázdným klíčem.</span><span class="sxs-lookup"><span data-stu-id="231b1-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="231b1-106">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="231b1-106">Mitigation</span></span>  
 <span data-ttu-id="231b1-107">Určuje, zda se zjistí Chyba ověření schématu, pokud složený klíč má jeden prázdný klíč je konfigurovat funkce:</span><span class="sxs-lookup"><span data-stu-id="231b1-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="231b1-108">Počínaje aplikací, které se zaměřují [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detekce chyby ověřování schématu je povolené ve výchozím nastavení; ale je možné vyjádřit výslovný nesouhlas, tak, že nebudou zjištěna chyba ověření platnosti schématu.</span><span class="sxs-lookup"><span data-stu-id="231b1-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="231b1-109">V aplikacích, které jsou spuštěny pod [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ale cílit [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a starší verze, ve výchozím nastavení není zjištěna chyba ověření schématu; je však možné zvolit tuto možnost, tak, aby chyba ověření schématu se zjistil.</span><span class="sxs-lookup"><span data-stu-id="231b1-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="231b1-110">Toto chování je možné nakonfigurovat pomocí <xref:System.AppContext> třídy definují hodnotu `System.Xml.IgnoreEmptyKeySequences` přepnout.</span><span class="sxs-lookup"><span data-stu-id="231b1-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="231b1-111">Protože přepnout výchozí hodnota je `false` (prázdná sekvence klíče nejsou ignorovány), aplikace, které cílí [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] můžete vyjádřit výslovný nesouhlas chování pomocí následujícího kódu nastavit hodnotu na přepínač na `true`:</span><span class="sxs-lookup"><span data-stu-id="231b1-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="231b1-112">Pro aplikace, které cílí [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a předchozími verzemi, protože přepnout výchozí hodnota je `true` (prázdná sekvence klíče jsou ignorovány), je možné k zajištění, že složený klíč s prázdným klíčem generování Chyba ověření schématu pomocí Následující kód k nastavte hodnotu na přepínač `false`.</span><span class="sxs-lookup"><span data-stu-id="231b1-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="231b1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="231b1-113">See also</span></span>

- [<span data-ttu-id="231b1-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="231b1-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
