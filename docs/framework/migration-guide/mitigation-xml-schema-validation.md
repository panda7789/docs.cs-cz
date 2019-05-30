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
# <a name="mitigation-xml-schema-validation"></a>Omezení rizik: Ověření schématu XML
V rozhraní .NET Framework 4.6 ověření schématu XSD rozpozná porušení omezení unique, pokud se používá složený klíč a jeden klíč je prázdný.  
  
## <a name="impact"></a>Dopad  
 Dopad této změny by měl být minimální: podle specifikace schématu, Chyba ověření schématu se očekává, pokud `xsd:unique` porušení pomocí složeného klíče s prázdným klíčem.  
  
## <a name="mitigation"></a>Zmírnění  
 Určuje, zda se zjistí Chyba ověření schématu, pokud složený klíč má jeden prázdný klíč je konfigurovat funkce:  
  
- Počínaje aplikací využívajících rozhraní .NET Framework 4.6, detekce chyby ověřování schématu je standardně povolená; ale je možné vyjádřit výslovný nesouhlas, tak, že nebudou zjištěna chyba ověření platnosti schématu.  
  
- V aplikacích pro spuštění v rozhraní .NET Framework 4.6, které cílí na rozhraní .NET Framework 4.5.2 a starší verze není ve výchozím nastavení; zjištěna chyba ověřování schématu ale je možné začít používat, tak, aby chyba ověření schématu se zjistil.  
  
 Toto chování je možné nakonfigurovat pomocí <xref:System.AppContext> třídy definují hodnotu `System.Xml.IgnoreEmptyKeySequences` přepnout. Protože přepnout výchozí hodnota je `false` (prázdná sekvence klíče nejsou ignorovány), aplikace, které cílí rozhraní .NET Framework 4.6 můžete vyjádřit výslovný nesouhlas chování pomocí následujícího kódu nastavit hodnotu na přepínač na `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Pro aplikace, které cílí na rozhraní .NET Framework 4.5.2 a starší verze, protože přepnout výchozí hodnota je `true` (prázdná sekvence klíče jsou ignorovány), je možné k zajištění, že složený klíč s prázdným klíčem generování Chyba ověření schématu pomocí Následující kód do nastavte hodnotu na přepínač `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
