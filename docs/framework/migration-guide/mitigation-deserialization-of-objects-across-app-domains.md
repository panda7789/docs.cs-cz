---
title: 'Omezení rizik: Deserializace objektů mezi doménami aplikace'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5424eac20992d87542bd8a9a27d5775483d64a60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633948"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a>Omezení rizik: Deserializace objektů mezi doménami aplikace
V některých případech, kdy aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace, vyvolá pokus o deserializaci objektů v rámci logického kontextu volání mezi doménami aplikace výjimku.  
  
## <a name="diagnosing-the-issue"></a>Diagnostika problému  
 Tento problém nastane při následující posloupnosti podmínek:  
  
1.  Aplikace používá dvě nebo více domén aplikace s různými základy cesty aplikace.  
  
2.  Některé typy jsou explicitně přidány do typu <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> voláním metody, jako je <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>. Tyto typy nejsou označeny jako serializovatelné a nejsou uloženy v globální mezipaměti sestavení (GAC).  
  
3.  Později se kód spuštěný v jiné doméně aplikace, než je výchozí doména, pokusí načíst hodnotu z konfiguračního souboru, nebo pomocí jazyka XML deserializuje objekt.  
  
4.  Aby proběhlo načtení z konfiguračního souboru nebo deserializace objektu, pokusí se objekt <xref:System.Xml.XmlReader> o přístup k systému konfigurace.  
  
5.  Pokud systém konfigurace ještě nebyl inicializován, je nutné dokončit jeho inicializaci. Mimo jiné to znamená, že modul runtime musí vytvořit stabilní cestu pro systém konfigurace, což se provádí takto:  
  
    1.  Hledá legitimaci nevýchozí domény aplikace.  
  
    2.  Pokusí se vypočítat legitimaci nevýchozí domény aplikace založené na výchozí doméně aplikace.  
  
    3.  Volání uskutečněné za účelem získání legitimace výchozí domény aplikace spustí volání napříč doménou aplikace z nevýchozí domény aplikace do výchozí domény aplikace.  
  
    4.  Jako součást kontraktu napříč doménami aplikace v rozhraní .NET Framework musí být obsah logického kontextu volání zařazen napříč hranicemi domény aplikace.  
  
6.  Vzhledem k tomu, že ve výchozí doméně aplikace nelze rozpoznat typy, které jsou součástí logického kontextu volání, je vyvolána výjimka.  
  
## <a name="mitigation"></a>Zmírnění  
 Chcete-li tento problém odstranit, postupujte takto:  
  
1.  Pokud je vyvolána výjimka, v zásobníku volání vyhledejte volání metody `get_Evidence`. Touto výjimkou může být jakkoli velká podmnožina výjimek, včetně výjimek <xref:System.IO.FileNotFoundException> a <xref:System.Runtime.Serialization.SerializationException>.  
  
2.  Určete místo v aplikaci, ve kterém nejsou do logického kontextu volání přidány žádné objekty, a přidejte následující kód:  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)
