---
title: Návrh události
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b257da73d33fae54ef464e9dd69906316b87fd88
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44127917"
---
# <a name="event-design"></a>Návrh události
Události jsou nejčastěji používané formuláři zpětná volání (konstrukce, které umožňují rozhraní pro volání do uživatelského kódu). Jiné mechanismy zpětné volání zahrnout členy, přičemž delegáty, virtuální členy a založeny na rozhraní modulů plug-in. Data z použitelnost studie označuje, že většina vývojářů je pohodlnější použití událostí, než které využívají jiné mechanismy zpětné volání. Události jsou krásně součástí sady Visual Studio a mnoha jazyků.  
  
 Je důležité si uvědomit, že existují dvě skupiny událostí: události vyvolané před stavu změny systému, volá se před událostmi a události vyvolané po změně stavu, volá se po události. Příkladem předběžné události může být `Form.Closing`, která je vyvolána před zavřením formuláře. Příkladem po události může být `Form.Closed`, která je vyvolána po zavření formuláře.  
  
 **✓ DO** použít termín "vyvolat" pro události místo "fire" nebo "spustit".  
  
 **✓ DO** použít <xref:System.EventHandler%601?displayProperty=nameWithType> místo ruční vytvoření nového delegáti má být použit jako obslužné rutiny událostí.  
  
 **✓ CONSIDER** pomocí podtřídou třídy <xref:System.EventArgs> jako argument událost, pokud si nejste zcela jisti událost nikdy nebudete potřebovat k provedení žádná data pro zpracování metody událostí v takovém případě můžete použít `EventArgs` typ přímo.  
  
 Pokud neodešlete rozhraní API pomocí `EventArgs` přímo, nikdy budete moct přidat žádná data k realizaci s událostí bez porušení kompatibilitu. Pokud používáte podtřídu, i pokud původně úplně prázdná, bude možné přidávat vlastnosti pro podtřídu v případě potřeby.  
  
 **✓ DO** použít chráněné virtuální metodu pro vyvolání každé události. To platí pouze pro nestatické události v nezapečetěné třídy, struktury, zapečetěné třídy ani statické události.  
  
 Cílem této metody je poskytnout způsob, jakým odvozené třídy za účelem zpracování události pomocí přepsání. Přepsání je flexibilnější, rychlejší a přirozenější způsob, jak zpracovat událostí třídy base v odvozených třídách. Název metody podle konvence by měla začínat řetězcem "On" a následovat název události.  
  
 Odvozené třídy můžete volat základní implementaci metody v jeho přepsání. Připravit pro tento bez zahrnutí zpracování v metodě, která je požadována pro základní třídu fungovat správně.  
  
 **✓ DO** trvat jeden parametr chráněná metoda, která vyvolává událost.  
  
 Parametr by měl být pojmenován `e` a by měl být typu Třída argumentů události.  
  
 **X DO NOT** předejte hodnotu null pro odesílatele při vyvolání nestatické události.  
  
 **✓ DO** předejte hodnotu null pro odesílatele při vyvolání statické události.  
  
 **X DO NOT** předejte jako parametr data událostí hodnotu null při vyvolání události.  
  
 Je třeba předat `EventArgs.Empty` Pokud nechcete předávat žádná data pro metodu zpracování událostí. Vývojáři očekávat, že tento parametr nechcete mít hodnotu null.  
  
 **✓ CONSIDER** vyvolávání událostí, které můžete zrušit koncového uživatele. To platí pouze pro před událostmi.  
  
 Použití <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> nebo jeho podtřídy jako argument události koncovému uživateli pro zrušení události.  
  
### <a name="custom-event-handler-design"></a>Obslužná rutina návrhu vlastní událost  
 Existují případy, ve kterém `EventHandler<T>` nelze použít, třeba když rozhraní musí fungovat s předchozími verzemi modulu CLR, který nepodporuje obecné typy. V takových případech může být potřeba navrhovat a vyvíjet vlastní událost obslužné rutiny delegáta.  
  
 **✓ DO** použít návratový typ void pro obslužné rutiny událostí.  
  
 Obslužné rutiny události můžete volat metody, případně pro více objektů zpracování více událostí. Pokud pro navrácení hodnoty byly povoleny metody zpracování událostí, by bylo více vrácených hodnot pro každé vyvolání události.  
  
 **✓ DO** použít `object` jako typ prvního parametru obslužné rutiny události a pojmenujte ji `sender`.  
  
 **✓ DO** použít <xref:System.EventArgs?displayProperty=nameWithType> nebo jeho podtřídou jako typ druhého parametru obslužné rutiny události a pojmenujte ji `e`.  
  
 **X DO NOT** mít více než dva parametry obslužných rutin událostí.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
