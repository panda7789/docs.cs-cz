---
title: 'Omezení rizik: Ověřování schématu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 7feed7de4a6c76f5f2ba0e2ea1c532aad6bde4de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126077"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="7feba-102">Omezení rizik: Ověřování schématu XML</span><span class="sxs-lookup"><span data-stu-id="7feba-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="7feba-103">V .NET Framework 4,6 ověřování schématu XSD detekuje porušení omezení UNIQUE, pokud je použit složený klíč a jeden klíč je prázdný.</span><span class="sxs-lookup"><span data-stu-id="7feba-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="7feba-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="7feba-104">Impact</span></span>  
 <span data-ttu-id="7feba-105">Dopad této změny by měl být minimální: v závislosti na specifikaci schématu je očekávána chyba ověřování schématu, pokud je `xsd:unique` narušeno pomocí složeného klíče s prázdným klíčem.</span><span class="sxs-lookup"><span data-stu-id="7feba-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="7feba-106">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="7feba-106">Mitigation</span></span>  
 <span data-ttu-id="7feba-107">Zda je zjištěna chyba ověřování schématu, pokud je složený klíč s jedním prázdným klíčem konfigurovatelné funkce:</span><span class="sxs-lookup"><span data-stu-id="7feba-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="7feba-108">Počínaje aplikacemi, které cílí na .NET Framework 4,6, je ve výchozím nastavení povolená detekce chyby ověřování schématu. je ale možné, že se z něj můžete odhlásit, takže se nezjistí chyba ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="7feba-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="7feba-109">V aplikacích, které běží pod .NET Framework 4,6, ale cílí na .NET Framework 4.5.2 a starší verze, se ve výchozím nastavení nedetekuje chyba ověřování schématu. je však možné se k němu přihlásit, aby se zjistila chyba ověřování schématu.</span><span class="sxs-lookup"><span data-stu-id="7feba-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="7feba-110">Toto chování lze nakonfigurovat pomocí třídy <xref:System.AppContext> pro definování hodnoty přepínače `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="7feba-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="7feba-111">Vzhledem k tomu, že je výchozí hodnota přepínače `false` (prázdné sekvence klíčů nejsou ignorovány), aplikace, které cílí na .NET Framework 4,6, se mohou odhlásit z chování pomocí následujícího kódu, který nastaví hodnotu přepínače na `true`:</span><span class="sxs-lookup"><span data-stu-id="7feba-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="7feba-112">U aplikací, které cílí na .NET Framework 4.5.2 a starší verze, protože je výchozí hodnota přepínače `true` (prázdné klíčové sekvence jsou ignorovány), je možné zajistit, aby složený klíč s prázdným klíčem vygeneroval chybu ověřování schématu pomocí Následující kód nastaví hodnotu přepínače na `false`.</span><span class="sxs-lookup"><span data-stu-id="7feba-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7feba-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7feba-113">See also</span></span>

- [<span data-ttu-id="7feba-114">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="7feba-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
