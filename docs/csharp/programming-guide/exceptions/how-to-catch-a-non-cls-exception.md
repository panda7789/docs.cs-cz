---
title: Jak zachytit výjimku nekompatibilní se specifikací CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 635cf0a9142f56dea4b2722fbf3f3eda505d85ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346280"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Jak zachytit výjimku nekompatibilní se specifikací CLS
Některé jazyky .NET, včetně C++/CLI, umožňují objektům <xref:System.Exception>vyvolat výjimky, které nejsou odvozeny z . Tyto výjimky se nazývají *výjimky bez specifikace CLS* nebo *jiné výjimky*. V c# nelze vyvolat výjimky bez CLS, ale můžete je zachytit dvěma způsoby:  
  
- V `catch (RuntimeWrappedException e)` bloku.
  
     Ve výchozím nastavení visual c# sestavení zachytí výjimky bez CLS jako zabalené výjimky. Tuto metodu použijte, pokud potřebujete přístup k původní výjimce, ke které lze přistupovat prostřednictvím vlastnosti. <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> Postup dále v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.  
  
- V rámci obecné catch bloku (catch blok bez typu výjimky `catch` zadán), který je umístěn za všechny ostatní bloky.
  
     Tuto metodu použijte, pokud chcete provést nějakou akci (například zápis do souboru protokolu) v reakci na výjimky bez specifikace CLS a nepotřebujete přístup k informacím o výjimce. Ve výchozím nastavení zaobění běžného jazyka runtime zabalí všechny výjimky. Chcete-li toto chování zakázat, přidejte do kódu tento `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`atribut na úrovni sestavení, obvykle v souboru AssemblyInfo.cs: .  
  
### <a name="to-catch-a-non-cls-exception"></a>Chcete-li zachytit výjimku bez specifikace CLS  
  
V `catch(RuntimeWrappedException e)` rámci bloku přístup k <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> původní výjimku prostřednictvím vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachytit výjimku bez specifikace CLS, která byla vyvolána z knihovny tříd napsané v jazyce C++/CLI. Všimněte si, že v tomto příkladu kód klienta C# <xref:System.String?displayProperty=nameWithType>předem ví, že typ výjimky je vyvolána . Můžete přetypovat <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> vlastnost zpět jeho původní typ tak dlouho, dokud tento typ je přístupný z vašeho kódu.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [Výjimky a zpracování výjimek](./index.md)
