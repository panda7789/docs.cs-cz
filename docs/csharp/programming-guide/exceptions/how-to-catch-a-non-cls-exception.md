---
title: Jak zachytit výjimku, která není CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346280"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Jak zachytit výjimku, která není CLS
Některé jazyky .NET, včetně C++/CLI, umožňují, aby objekty vyvolaly výjimky, které nejsou odvozeny od <xref:System.Exception>. Takové výjimky se nazývají *výjimky, které nejsou kompatibilní se specifikací CLS* , nebo *nevýjimkou*. V C# nemůžete vyvolat výjimky, které nejsou kompatibilní se specifikací CLS, ale můžete je zachytit dvěma způsoby:  
  
- V rámci `catch (RuntimeWrappedException e)`ho bloku.
  
     Ve výchozím nastavení je sestavení C# sady Visual zachytí výjimky NEODPOVÍDAJÍCÍ specifikaci CLS jako zabalené výjimky. Tuto metodu použijte, pokud potřebujete přístup k původní výjimce, ke které lze přistupovat prostřednictvím vlastnosti <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>. Postup dále v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.  
  
- V rámci obecného bloku catch (je určen blok catch bez typu výjimky), který je umístěn po všech ostatních `catch` blocích.
  
     Tuto metodu použijte, pokud chcete provést určitou akci (například zápis do souboru protokolu) v reakci na výjimky jiné než CLS a nepotřebujete přístup k informacím o výjimkách. Ve výchozím nastavení jsou všechny výjimky zabaleny modulem CLR (Common Language Runtime). Chcete-li toto chování zakázat, přidejte do kódu tento atribut na úrovni sestavení, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>Zachycení výjimky nesouvisející se specifikací CLS  
  
V rámci `catch(RuntimeWrappedException e)` bloku přístup k původní výjimce prostřednictvím vlastnosti <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachytit výjimku, která není CLS, která byla vyvolána z knihovny tříd napsané v C++/CLI. Všimněte si, že v tomto příkladu C# kód klienta ví, že typ výjimky, která je vyvolána, je <xref:System.String?displayProperty=nameWithType>. Vlastnost <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> můžete přetypovat zpět na původní typ, pokud je tento typ přístupný z vašeho kódu.  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [Výjimky a jejich zpracování](./index.md)
