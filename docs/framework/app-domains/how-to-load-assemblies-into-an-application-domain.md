---
title: 'Postupy: Načtení sestavení do domény aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c560e2c5858de67442ccbcd18c8f92b142cc178d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119897"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Postupy: Načtení sestavení do domény aplikace
Existuje několik způsobů, jak načíst sestavení do domény aplikace. Doporučeným způsobem je použít `static` metodu (`Shared` v Visual Basic) <xref:System.Reflection.Assembly.Load%2A> <xref:System.Reflection.Assembly?displayProperty=nameWithType> třídy. Další způsoby, jak lze načíst sestavení, zahrnují:  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> Metoda <xref:System.Reflection.Assembly> třídy načte sestavení příslušné umístění souboru. Načítání sestavení s touto metodou používá jiný kontext zatížení.  
  
- Metody <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> načtou sestavení do kontextu pouze pro reflexi. Sestavení, která jsou načtena do tohoto kontextu, lze prozkoumat, ale nejsou provedena, a umožnit tak zkoumání sestavení, která cílí na jiné platformy. Viz [Postupy: načtení sestavení do kontextu pouze pro reflexi](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
> Kontext pouze pro reflexi je v .NET Framework verze 2,0 nový.  
  
- Metody jako <xref:System.AppDomain.CreateInstance%2A> a <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> <xref:System.AppDomain> třídy mohou načítat sestavení do domény aplikace.  
  
- <xref:System.Type.GetType%2A> Metoda <xref:System.Type> třídy může načíst sestavení.  
  
- <xref:System.AppDomain.Load%2A> Metoda <xref:System.AppDomain?displayProperty=nameWithType> třídy může načíst sestavení, ale používá se hlavně pro interoperabilitu modelu COM. Neměl by být použit pro načtení sestavení do domény aplikace jiné než domény aplikace, ze které je volána.  
  
> [!NOTE]
> Počínaje verzí 2,0 .NET Framework modul runtime nenačte sestavení, které bylo zkompilováno s verzí .NET Framework, která má vyšší číslo verze než aktuálně načtený modul runtime. To platí pro kombinaci hlavních a vedlejších součástí čísla verze.  
  
 Můžete určit způsob, jakým je zkompilovaný kód JIT (just-in-time) z načtených sestavení sdílen mezi doménami aplikace. Další informace naleznete v tématu [aplikační domény a sestavení](application-domains.md#application-domains-and-assemblies).  
  
## <a name="example"></a>Příklad  
 Následující kód načte sestavení s názvem "example. exe" nebo "example. dll" do aktuální domény aplikace, získá typ pojmenovaný `Example` ze sestavení, získá metodu bez parametrů pojmenovanou `MethodA` pro daný typ a spustí metodu. Kompletní diskuzi o získání informací z načteného sestavení naleznete v tématu [Dynamické načítání a používání typů](../reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [Programování s aplikačními doménami](application-domains.md#programming-with-application-domains)
- [Reflexe](../reflection-and-codedom/reflection.md)
- [Používání domén aplikací](use.md)
- [Postupy: Načtení sestavení do kontextu pouze pro reflexi](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [Domény a sestavení aplikací](application-domains.md#application-domains-and-assemblies)
