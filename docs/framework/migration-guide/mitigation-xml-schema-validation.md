---
title: 'Omezení rizik: Ověření schématu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbeeecda3bd34f5eb651cb32246f8b56d5705002
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651003"
---
# <a name="mitigation-xml-schema-validation"></a>Omezení rizik: Ověření schématu XML
V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], ověření schématu XSD rozpozná porušení omezení unique, pokud se používá složený klíč a jeden klíč je prázdný.  
  
## <a name="impact"></a>Dopad  
 Dopad této změny by měl být minimální: podle specifikace schématu, Chyba ověření schématu se očekává, pokud `xsd:unique` porušení pomocí složeného klíče s prázdným klíčem.  
  
## <a name="mitigation"></a>Zmírnění  
 Určuje, zda se zjistí Chyba ověření schématu, pokud složený klíč má jeden prázdný klíč je konfigurovat funkce:  
  
-   Počínaje aplikací, které se zaměřují [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detekce chyby ověřování schématu je povolené ve výchozím nastavení; ale je možné vyjádřit výslovný nesouhlas, tak, že nebudou zjištěna chyba ověření platnosti schématu.  
  
-   V aplikacích, které jsou spuštěny pod [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ale cílit [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a starší verze, ve výchozím nastavení není zjištěna chyba ověření schématu; je však možné zvolit tuto možnost, tak, aby chyba ověření schématu se zjistil.  
  
 Toto chování je možné nakonfigurovat pomocí <xref:System.AppContext> třídy definují hodnotu `System.Xml.IgnoreEmptyKeySequences` přepnout. Protože přepnout výchozí hodnota je `false` (prázdná sekvence klíče nejsou ignorovány), aplikace, které cílí [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] můžete vyjádřit výslovný nesouhlas chování pomocí následujícího kódu nastavit hodnotu na přepínač na `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Pro aplikace, které cílí [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a předchozími verzemi, protože přepnout výchozí hodnota je `true` (prázdná sekvence klíče jsou ignorovány), je možné k zajištění, že složený klíč s prázdným klíčem generování Chyba ověření schématu pomocí Následující kód k nastavte hodnotu na přepínač `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
