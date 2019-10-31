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
# <a name="mitigation-xml-schema-validation"></a>Omezení rizik: Ověřování schématu XML
V .NET Framework 4,6 ověřování schématu XSD detekuje porušení omezení UNIQUE, pokud je použit složený klíč a jeden klíč je prázdný.  
  
## <a name="impact"></a>Dopad  
 Dopad této změny by měl být minimální: v závislosti na specifikaci schématu je očekávána chyba ověřování schématu, pokud je `xsd:unique` narušeno pomocí složeného klíče s prázdným klíčem.  
  
## <a name="mitigation"></a>Zmírnění  
 Zda je zjištěna chyba ověřování schématu, pokud je složený klíč s jedním prázdným klíčem konfigurovatelné funkce:  
  
- Počínaje aplikacemi, které cílí na .NET Framework 4,6, je ve výchozím nastavení povolená detekce chyby ověřování schématu. je ale možné, že se z něj můžete odhlásit, takže se nezjistí chyba ověřování schématu.  
  
- V aplikacích, které běží pod .NET Framework 4,6, ale cílí na .NET Framework 4.5.2 a starší verze, se ve výchozím nastavení nedetekuje chyba ověřování schématu. je však možné se k němu přihlásit, aby se zjistila chyba ověřování schématu.  
  
 Toto chování lze nakonfigurovat pomocí třídy <xref:System.AppContext> pro definování hodnoty přepínače `System.Xml.IgnoreEmptyKeySequences`. Vzhledem k tomu, že je výchozí hodnota přepínače `false` (prázdné sekvence klíčů nejsou ignorovány), aplikace, které cílí na .NET Framework 4,6, se mohou odhlásit z chování pomocí následujícího kódu, který nastaví hodnotu přepínače na `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 U aplikací, které cílí na .NET Framework 4.5.2 a starší verze, protože je výchozí hodnota přepínače `true` (prázdné klíčové sekvence jsou ignorovány), je možné zajistit, aby složený klíč s prázdným klíčem vygeneroval chybu ověřování schématu pomocí Následující kód nastaví hodnotu přepínače na `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6.md)
