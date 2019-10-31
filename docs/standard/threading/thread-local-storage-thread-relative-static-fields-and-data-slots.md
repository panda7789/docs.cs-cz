---
title: 'Lokální úložiště vláken: statická pole a datové sloty ve vztahu k vláknům'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
ms.openlocfilehash: b5a7c4b78f8599f64aa11f1c98c033866e582933
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127525"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Lokální úložiště vláken: statická pole a datové sloty ve vztahu k vláknům
Pomocí spravovaného úložiště thread local (TLS) můžete ukládat data, která jsou jedinečná pro vlákno a doménu aplikace. .NET Framework poskytuje dva způsoby použití spravovaného TLS: statická pole a datové sloty související s vláknem.  
  
- Použijte statická pole související s vlákny (pole `Shared` relativních k vláknům v Visual Basic), pokud můžete v době kompilace odhadnout vaše přesné potřeby. Statická pole, která jsou v závislosti na vláknech, poskytují nejlepší výkon. Poskytují vám také výhody kontroly typu při kompilaci.  
  
- Datové sloty můžete použít, pokud vaše skutečné požadavky mohou být zjištěny pouze v době běhu. Datové sloty jsou pomalejší a lépe nenáročné na použití než statická pole v závislosti na vláknech a data jsou ukládána jako typ <xref:System.Object>, takže je musíte přetypovat na správný typ předtím, než je použijete.  
  
 V nespravovaném C++případě použijete `TlsAlloc` k dynamickému přidělování slotů a `__declspec(thread)` deklarovat, že by měla být proměnná přidělena v úložišti relativním pro vlákno. Statická pole a datové sloty související s vláknem poskytují spravovanou verzi tohoto chování.  
  
 V .NET Framework 4 můžete použít třídu <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> k vytvoření místních objektů vlákna, které jsou inicializovány laxně vytvářená při prvním použití objektu. Další informace naleznete v tématu [opožděná inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Jedinečnost dat ve spravovaném TLS  
 Bez ohledu na to, jestli používáte statická pole nebo datové sloty související s vláknem, jsou data v spravovaném TLS jedinečná pro kombinaci vlákna a domény aplikace.  
  
- V rámci domény aplikace nemůže jedno vlákno upravovat data z jiného vlákna, a to i v případě, že obě vlákna používají stejné pole nebo slot.  
  
- Když vlákno přistupuje ke stejnému poli nebo pozici z více domén aplikace, zachová se v každé doméně aplikace samostatná hodnota.  
  
 Například pokud vlákno nastaví hodnotu statického pole relativního k vláknu, přejde do jiné aplikační domény a potom načte hodnotu pole, hodnota načtená v druhé doméně aplikace se liší od hodnoty v první doméně aplikace. Nastavení nové hodnoty pro pole v druhé aplikační doméně nemá vliv na hodnotu pole v první aplikační doméně.  
  
 Podobně, pokud vlákno získá stejnou pojmenovanou datovou oblast ve dvou různých aplikačních doménách, data v první aplikační doméně zůstanou nezávislá na datech v druhé aplikační doméně.  
  
## <a name="thread-relative-static-fields"></a>Statická pole v závislosti na vláknech  
 Pokud víte, že část dat je vždy jedinečná pro kombinaci vlákna a domény aplikace, použijte atribut <xref:System.ThreadStaticAttribute> pro statické pole. Použijte pole, jako byste použili jiné statické pole. Data v poli jsou jedinečná pro každé vlákno, které ho používá.  
  
 Statická pole v závislosti na vláknech poskytují lepší výkon než datové sloty a mají výhodu kontroly typu při kompilaci.  
  
 Mějte na paměti, že jakýkoliv kód konstruktoru třídy se spustí v prvním vlákně v prvním kontextu, který přistupuje k poli. Ve všech ostatních vláknech nebo kontextech ve stejné doméně aplikace budou pole inicializována na `null` (`Nothing` v Visual Basic), pokud se jedná o typy odkazů nebo na jejich výchozí hodnoty, pokud jsou typy hodnot. Proto byste neměli spoléhat na konstruktory třídy pro inicializaci statických polí relativních k vláknům. Místo toho Vyhněte se inicializaci statických polí relativních ke vláknům a předpokládat, že jsou inicializovány na `null` (`Nothing`) nebo na jejich výchozí hodnoty.  
  
## <a name="data-slots"></a>Datové sloty  
 .NET Framework poskytuje dynamické datové sloty, které jsou jedinečné pro kombinaci vlákna a aplikační domény. Existují dva typy datových slotů: pojmenované sloty a nepojmenované sloty. Obě jsou implementovány pomocí <xref:System.LocalDataStoreSlot> struktury.  
  
- Chcete-li vytvořit pojmenovanou datovou oblast, použijte metodu <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>. Chcete-li získat odkaz na existující pojmenovanou pozici, předejte svůj název metodě <xref:System.Threading.Thread.GetNamedDataSlot%2A>.  
  
- Chcete-li vytvořit nepojmenované datové sloty, použijte metodu <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType>.  
  
 Pro pojmenované i nepojmenované sloty použijte metody <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> k nastavení a načtení informací v patici. Jedná se o statické metody, které vždy pracují s daty pro vlákno, které je právě spouští.  
  
 Pojmenované sloty můžou být pohodlné, protože můžete načíst slot, když ho potřebujete, předáním jeho názvu metodě <xref:System.Threading.Thread.GetNamedDataSlot%2A>, namísto udržování odkazu na nepojmenované slot. Pokud však jiná komponenta používá stejný název pro své relativní úložiště vlákna a vlákno spustí kód z vaší komponenty i druhé komponenty, mohou tyto dvě součásti poškodit data každé druhé. (Tento scénář předpokládá, že obě komponenty jsou spuštěné ve stejné aplikační doméně a že nejsou navržené tak, aby sdílely stejná data.)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [Dělení na vlákna](../../../docs/standard/threading/index.md)
