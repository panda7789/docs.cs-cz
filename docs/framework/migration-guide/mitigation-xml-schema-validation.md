---
title: 'Omezení rizik: Ověření schématu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36f9475a978ddf7253833e6c3372049d24502f95
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300575"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="20aaa-102">Omezení rizik: Ověření schématu XML</span><span class="sxs-lookup"><span data-stu-id="20aaa-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="20aaa-103">V rozhraní .NET Framework 4.6 ověření schématu XSD rozpozná porušení omezení unique, pokud se používá složený klíč a jeden klíč je prázdný.</span><span class="sxs-lookup"><span data-stu-id="20aaa-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="20aaa-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="20aaa-104">Impact</span></span>  
 <span data-ttu-id="20aaa-105">Dopad této změny by měl být minimální: podle specifikace schématu, Chyba ověření schématu se očekává, pokud `xsd:unique` porušení pomocí složeného klíče s prázdným klíčem.</span><span class="sxs-lookup"><span data-stu-id="20aaa-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="20aaa-106">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="20aaa-106">Mitigation</span></span>  
 <span data-ttu-id="20aaa-107">Určuje, zda se zjistí Chyba ověření schématu, pokud složený klíč má jeden prázdný klíč je konfigurovat funkce:</span><span class="sxs-lookup"><span data-stu-id="20aaa-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="20aaa-108">Počínaje aplikací využívajících rozhraní .NET Framework 4.6, detekce chyby ověřování schématu je standardně povolená; ale je možné vyjádřit výslovný nesouhlas, tak, že nebudou zjištěna chyba ověření platnosti schématu.</span><span class="sxs-lookup"><span data-stu-id="20aaa-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="20aaa-109">V aplikacích pro spuštění v rozhraní .NET Framework 4.6, které cílí na rozhraní .NET Framework 4.5.2 a starší verze není ve výchozím nastavení; zjištěna chyba ověřování schématu ale je možné začít používat, tak, aby chyba ověření schématu se zjistil.</span><span class="sxs-lookup"><span data-stu-id="20aaa-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="20aaa-110">Toto chování je možné nakonfigurovat pomocí <xref:System.AppContext> třídy definují hodnotu `System.Xml.IgnoreEmptyKeySequences` přepnout.</span><span class="sxs-lookup"><span data-stu-id="20aaa-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="20aaa-111">Protože přepnout výchozí hodnota je `false` (prázdná sekvence klíče nejsou ignorovány), aplikace, které cílí rozhraní .NET Framework 4.6 můžete vyjádřit výslovný nesouhlas chování pomocí následujícího kódu nastavit hodnotu na přepínač na `true`:</span><span class="sxs-lookup"><span data-stu-id="20aaa-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="20aaa-112">Pro aplikace, které cílí na rozhraní .NET Framework 4.5.2 a starší verze, protože přepnout výchozí hodnota je `true` (prázdná sekvence klíče jsou ignorovány), je možné k zajištění, že složený klíč s prázdným klíčem generování Chyba ověření schématu pomocí Následující kód do nastavte hodnotu na přepínač `false`.</span><span class="sxs-lookup"><span data-stu-id="20aaa-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="20aaa-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20aaa-113">See also</span></span>

- [<span data-ttu-id="20aaa-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="20aaa-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
