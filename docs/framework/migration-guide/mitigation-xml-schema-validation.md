---
title: "Omezení rizik: Ověřování schématu XML"
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
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8bc8aab23490b5531a155798520936cacbd6a6d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="45e20-102">Omezení rizik: Ověřování schématu XML</span><span class="sxs-lookup"><span data-stu-id="45e20-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="45e20-103">V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], ověření schématu XSD zjistí porušení jedinečné omezení, pokud je použit složený klíč a jeden klíč je prázdný.</span><span class="sxs-lookup"><span data-stu-id="45e20-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="45e20-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="45e20-104">Impact</span></span>  
 <span data-ttu-id="45e20-105">Dopad tato změna by měl být minimální: na základě schématu specifikace, chybu ověření schématu se očekává, pokud `xsd:unique` porušení pomocí složeného klíče s prázdným klíčem.</span><span class="sxs-lookup"><span data-stu-id="45e20-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="45e20-106">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="45e20-106">Mitigation</span></span>  
 <span data-ttu-id="45e20-107">Jestli se zjistí chybu ověření schématu, pokud má složený klíč jeden prázdný klíč je konfigurovat funkce:</span><span class="sxs-lookup"><span data-stu-id="45e20-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
-   <span data-ttu-id="45e20-108">Od verze aplikace cílených [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], ve výchozím nastavení je povoleno vyhledávání chybu ověření schématu; ale je možné, pro vyjádření výslovného nesouhlasu, takže nebudou zjištěna chyba ověření schématu.</span><span class="sxs-lookup"><span data-stu-id="45e20-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
-   <span data-ttu-id="45e20-109">V aplikacích, které běží pod [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] cíle, ale [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a starší verze, ve výchozím nastavení není zjištěna chyba ověření schématu; ale je možné, který se přidá do, tak, že bude zjištěna chyba ověření schématu.</span><span class="sxs-lookup"><span data-stu-id="45e20-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="45e20-110">Toto chování se dá nakonfigurovat pomocí <xref:System.AppContext> třídy definují hodnotu `System.Xml.IgnoreEmptyKeySequences` přepínače.</span><span class="sxs-lookup"><span data-stu-id="45e20-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="45e20-111">Protože přepínač na výchozí hodnota je `false` (prázdný posloupnosti kláves nejsou ignorovat), aplikace, které cílí [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] můžete vyjádření výslovného nesouhlasu chování pomocí následující kód k nastavení hodnoty na přepínač na `true`:</span><span class="sxs-lookup"><span data-stu-id="45e20-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="45e20-112">Pro aplikace, které cílí [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a starší verze, protože na přepínač Výchozí hodnota je `true` (prázdný posloupnosti kláves ignorují), je možné zajistit, že složené klíče s prázdným klíčem generovat chybu ověření schématu pomocí Následující kód k nastavení hodnoty na přepínač na `false`.</span><span class="sxs-lookup"><span data-stu-id="45e20-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="45e20-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="45e20-113">See Also</span></span>  
 [<span data-ttu-id="45e20-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="45e20-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
