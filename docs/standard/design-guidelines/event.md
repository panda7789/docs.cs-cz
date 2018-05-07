---
title: Návrh událostí
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
ms.openlocfilehash: 48d1ad0f02ae34675c0a910d7651d718c060db60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="event-design"></a>Návrh událostí
Události jsou nejčastěji používané formu zpětných volání (konstrukce, které umožňují rozhraní k volání do kódu uživatele). Další mechanismy zpětné volání zahrnout členy trvá delegáti, virtuální členové a na základě rozhraní moduly plug-in. Data z použitelnost studie označit, že většina vývojářů pohodlnější použití událostí, než používají jiné mechanismy zpětné volání. Události jsou výborně integrované s Visual Studio a mnoha jazycích.  
  
 Je důležité si uvědomit, že existují dvě skupiny události: událostí vyvolaných před stavu změny systému, volá se před události a události aktivované po změn stavu, volá se po události. Příkladem předběžné události může být `Form.Closing`, která je vyvolána před zavřením formuláře. Jedná se například po události `Form.Closed`, která se vyvolá po zavření formuláře.  
  
 **PROVEĎTE ✓** použít termín "vyvolat" pro události místo "fire" nebo "spustit".  
  
 **PROVEĎTE ✓** použít <xref:System.EventHandler%601?displayProperty=nameWithType> místo ruční vytvoření nového delegáti má být použit jako obslužné rutiny událostí.  
  
 **✓ ZVAŽTE** pomocí podtřídou třídy <xref:System.EventArgs> jako argument událost, pokud si nejste zcela jisti událost nikdy nebudete potřebovat k provedení žádná data pro zpracování metody událostí v takovém případě můžete použít `EventArgs` typ přímo.  
  
 Pokud dodávat rozhraní API pomocí `EventArgs` přímo, nikdy nebudete moct přidat žádná data k realizaci k události, aniž by vás kompatibility. Pokud používáte podtřídy, i pokud původně úplně prázdná, nebudete moct přidávat vlastnosti pro podtřídu v případě potřeby.  
  
 **PROVEĎTE ✓** použít chráněné virtuální metodu pro vyvolání každé události. Tento krok platí jenom pro nestatické událostí v nezapečetěných třídy, struktury, zapečetěné třídy ani statické události.  
  
 Cílem této metody je poskytnout způsob, jak odvozené třídy za účelem zpracování události pomocí přepsání. Přepsání je flexibilnější, rychlejší a přirozenější způsob zpracování událostí třídy base v odvozených třídách. Podle konvence název metody by měla začínat znakem "Na" a provést s názvem události.  
  
 Odvozené třídy mohou rozhodnout volat základní implementaci metody v jeho přepsání. Připravit pro tento není zahrnutím jakékoli zpracovávání v metodě, které jsou potřeba pro základní třídu fungovala správně.  
  
 **PROVEĎTE ✓** trvat jeden parametr chráněná metoda, která vyvolává událost.  
  
 Parametr musí mít název `e` a by měla být zadána jako třída argumentů události.  
  
 **X nesmí** předejte hodnotu null pro odesílatele při vyvolání nestatické události.  
  
 **PROVEĎTE ✓** předejte hodnotu null pro odesílatele při vyvolání statické události.  
  
 **X nesmí** předejte jako parametr data událostí hodnotu null při vyvolání události.  
  
 By měla předávat `EventArgs.Empty` Pokud nechcete, aby všechny data předat metodu zpracování událostí. Vývojáři očekávají, že tento parametr nechcete mít hodnotu null.  
  
 **✓ ZVAŽTE** vyvolávání událostí, které můžete zrušit koncového uživatele. To platí jenom pro předběžné události.  
  
 Použití <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> nebo jeho podtřídou jako argument události koncovému uživateli se zrušit události.  
  
### <a name="custom-event-handler-design"></a>Obslužná rutina návrhu vlastní události  
 Existují případy, ve kterém `EventHandler<T>` nelze použít, například když rozhraní potřebuje pro starší verze modulu CLR, který nepodporuje obecné typy. V takových případech může být nutné pro návrh a vývoj vlastní události delegáta obslužné rutiny.  
  
 **PROVEĎTE ✓** použít návratový typ void pro obslužné rutiny událostí.  
  
 Obslužné rutiny události můžete vyvolat metody, které by mohly mít na více objektů zpracování více událostí. Pokud bude vrácena hodnota byly povoleny metody zpracování událostí, by bylo více vrácených hodnot pro každé vyvolání události.  
  
 **PROVEĎTE ✓** použít `object` jako typ prvního parametru obslužné rutiny události a pojmenujte ji `sender`.  
  
 **PROVEĎTE ✓** použít <xref:System.EventArgs?displayProperty=nameWithType> nebo jeho podtřídou jako typ druhého parametru obslužné rutiny události a pojmenujte ji `e`.  
  
 **X nesmí** mít více než dva parametry obslužných rutin událostí.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu člena](../../../docs/standard/design-guidelines/member.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
