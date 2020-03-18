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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127525"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Lokální úložiště vláken: statická pole a datové sloty ve vztahu k vláknům
Místní úložiště spravovaného vlákna (TLS) můžete použít k ukládání dat, která jsou jedinečná pro vlákno a doménu aplikace. Rozhraní .NET Framework poskytuje dva způsoby použití spravovaného tls: statická pole relativní k vláknu a datové sloty.  
  
- Pokud můžete předvídat přesné potřeby `Shared` v době kompilace, použijte statická pole relativní pro vlákno (pole relativní pod proces v jazyce Visual Basic). Statická pole relativní k vláknu poskytují nejlepší výkon. Poskytují také výhody kontroly typu kompilace.  
  
- Datové sloty používejte v případě, že vaše skutečné požadavky mohou být zjištěny pouze za běhu. Datové sloty jsou pomalejší a nepříjemnější než statická pole relativní k <xref:System.Object>vláknu a data jsou uložena jako typ , takže je nutné je před použitím přetypovat na správný typ.  
  
 V nespravovaném jazyce `TlsAlloc` C++ slouží k `__declspec(thread)` dynamickému přidělování slotů a k deklarování, že proměnná by měla být přidělena v úložišti relativním k vláknu. Statická pole a datové sloty relativní k vláknu poskytují spravovanou verzi tohoto chování.  
  
 V rozhraní .NET Framework 4 <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> můžete použít třídu k vytvoření místních objektů podprocesů, které jsou inicializovány líně při prvním spotřebování objektu. Další informace naleznete [v tématu Opožděná inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Jedinečnost dat ve spravovaném tls  
 Bez ohledu na to, zda používáte statická pole relativní pro vlákno nebo datové sloty, data ve spravovaném tls jsou jedinečná pro kombinaci vlákna a domény aplikace.  
  
- V rámci domény aplikace jedno vlákno nemůže upravovat data z jiného vlákna, i když obě vlákna používají stejné pole nebo patici.  
  
- Když vlákno přistupuje ke stejnému poli nebo patice z více aplikačních domén, je v každé doméně aplikace zachována samostatná hodnota.  
  
 Pokud například vlákno nastaví hodnotu statického pole relativního k vláknu, zadá jinou doménu aplikace a pak načte hodnotu pole, hodnota načtená v druhé doméně aplikace se liší od hodnoty v první doméně aplikace. Nastavení nové hodnoty pro pole v druhé doméně aplikace nemá vliv na hodnotu pole v první doméně aplikace.  
  
 Podobně když vlákno získá stejný pojmenovaný datový slot ve dvou různých aplikačních doménách, data v první doméně aplikace zůstanou nezávislá na datech v druhé doméně aplikace.  
  
## <a name="thread-relative-static-fields"></a>Statická pole relativní k vláknu  
 Pokud víte, že část dat je vždy jedinečná pro kombinaci <xref:System.ThreadStaticAttribute> vlákna a aplikace a domény, použijte atribut na statické pole. Použijte toto pole stejně jako jakékoli jiné statické pole. Data v poli jsou jedinečná pro každé vlákno, které je používá.  
  
 Statická pole relativní k vláknům poskytují lepší výkon než datové sloty a mají výhodu kontroly typu kompilace.  
  
 Uvědomte si, že jakýkoli kód konstruktoru třídy bude spuštěn v prvním vlákně v prvním kontextu, který přistupuje k poli. Ve všech ostatních vláknech nebo kontextech ve stejné doméně `null` `Nothing` aplikace budou pole inicializována do (v jazyce Visual Basic), pokud jsou to typy odkazů, nebo na jejich výchozí hodnoty, pokud se jedná o typy hodnot. Proto byste neměli spoléhat na konstruktory třídy k inicializaci statických polí relativních k vláknu. Místo toho se vyhněte inicializaci statických `null` polí`Nothing`relativních k vláknu a předpokládejme, že jsou inicializována na ( ) nebo na jejich výchozí hodnoty.  
  
## <a name="data-slots"></a>Datové sloty  
 Rozhraní .NET Framework poskytuje dynamické datové sloty, které jsou jedinečné pro kombinaci vlákna a domény aplikace. Existují dva typy datových slotů: pojmenované sloty a nepojmenované sloty. Obě jsou implementovány <xref:System.LocalDataStoreSlot> pomocí struktury.  
  
- Chcete-li vytvořit pojmenovanou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> datovou patku, použijte metodu nebo. Chcete-li získat odkaz na existující pojmenovaný slot, předajte jeho název metodě. <xref:System.Threading.Thread.GetNamedDataSlot%2A>  
  
- Chcete-li vytvořit nepojmenovaný datový <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> slot, použijte metodu.  
  
 Pro pojmenované i nepojmenované sloty <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> použijte metody a nastavte a načtěte informace v patici. Jedná se o statické metody, které vždy působí na data pro vlákno, které je aktuálně provádí.  
  
 Pojmenované sloty mohou být pohodlné, protože můžete načíst slot, když <xref:System.Threading.Thread.GetNamedDataSlot%2A> ji potřebujete, předáním jeho názvu metodě, namísto zachování odkazu na nepojmenovanou patici. Pokud však jiná komponenta používá stejný název pro své úložiště relativní k vláknu a vlákno spustí kód z komponenty i z druhé součásti, mohou být obě součásti navzájem poškozeny. (Tento scénář předpokládá, že obě součásti jsou spuštěny ve stejné doméně aplikace a že nejsou navrženy tak, aby sdílet stejná data.)  
  
## <a name="see-also"></a>Viz také

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [Threading](../../../docs/standard/threading/index.md)
