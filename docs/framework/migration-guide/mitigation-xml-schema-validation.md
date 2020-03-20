---
title: 'Omezení rizik: Ověřování schématu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457749"
---
# <a name="mitigation-xml-schema-validation"></a>Omezení rizik: Ověřování schématu XML
V rozhraní .NET Framework 4.6 ověření schématu XSD zjistí porušení jedinečné omezení, pokud je použit složený klíč a jeden klíč je prázdný.  
  
## <a name="impact"></a>Dopad  
 Dopad této změny by měl být minimální: na základě specifikace schématu se očekává `xsd:unique` chyba ověření schématu, pokud je porušena pomocí složeného klíče s prázdným klíčem.  
  
## <a name="mitigation"></a>Omezení rizik  
 To, zda je zjištěna chyba ověření schématu, pokud složený klíč obsahuje jeden prázdný klíč, je konfigurovatelná funkce:  
  
- Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6, je ve výchozím nastavení povoleno zjišťování chyby ověření schématu. je však možné se od hlásit, takže nebude zjištěna chyba ověření schématu.  
  
- V aplikacích, které běží v rámci rozhraní .NET Framework 4.6, ale cílí na rozhraní .NET Framework 4.5.2 a starší verze, není ve výchozím nastavení zjištěna chyba ověření schématu. je však možné se do něj přihlásit, aby byla zjištěna chyba ověření schématu.  
  
 Toto chování lze nakonfigurovat pomocí třídy <xref:System.AppContext> `System.Xml.IgnoreEmptyKeySequences` k definování hodnoty přepínače. Vzhledem k tomu, `false` že výchozí hodnota přepínače je (prázdné posloupnosti kláves nejsou ignorovány), aplikace, které cílí na rozhraní .NET Framework 4.6, se mohou odhlásit z chování pomocí následujícího kódu pro nastavení hodnoty přepínače na `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 U aplikací, které cílí na rozhraní .NET Framework 4.5.2 a `true` starší verze, protože výchozí hodnota přepínače je (prázdné klíčové sekvence jsou ignorovány), je možné zajistit, aby složený klíč s `false`prázdným klíčem generoval chybu ověření schématu pomocí následujícího kódu pro nastavení hodnoty přepínače na .  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
