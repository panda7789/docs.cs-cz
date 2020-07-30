---
title: Jak zachytit výjimku nekompatibilní se specifikací CLS
description: Naučte se zachytit výjimku, která není CLS. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 255de4cab9a72491eb3b9624d968539d432e0442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302006"
---
# <a name="how-to-catch-a-non-cls-exception"></a>Jak zachytit výjimku nekompatibilní se specifikací CLS
Některé jazyky .NET, včetně C++/CLI, umožňují, aby objekty vyvolaly výjimky, které nejsou odvozeny od <xref:System.Exception> . Takové výjimky se nazývají *výjimky, které nejsou kompatibilní se specifikací CLS* , nebo *nevýjimkou*. V jazyce C# nelze vyvolat výjimky, které nejsou kompatibilní se specifikací CLS, ale můžete je zachytit dvěma způsoby:  
  
- V rámci `catch (RuntimeWrappedException e)` bloku.
  
     Ve výchozím nastavení sestavení Visual C# zachycuje výjimky nepatřící do CLS jako zabalené výjimky. Tuto metodu použijte, pokud potřebujete přístup k původní výjimce, ke které lze přistupovat prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> Vlastnosti. Postup dále v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.  
  
- V rámci obecného bloku catch (je určen blok catch bez typu výjimky), který je umístěn po všech ostatních `catch` blocích.
  
     Tuto metodu použijte, pokud chcete provést určitou akci (například zápis do souboru protokolu) v reakci na výjimky jiné než CLS a nepotřebujete přístup k informacím o výjimkách. Ve výchozím nastavení jsou všechny výjimky zabaleny modulem CLR (Common Language Runtime). Chcete-li toto chování zakázat, přidejte do kódu tento atribut na úrovni sestavení, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` .  
  
### <a name="to-catch-a-non-cls-exception"></a>Zachycení výjimky nesouvisející se specifikací CLS  
  
V rámci `catch(RuntimeWrappedException e)` bloku přístup k původní výjimce prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> Vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachytit výjimku nekompatibilní se specifikací CLS vyvolanou z knihovny tříd napsanou v jazyce C++/CLI. Všimněte si, že v tomto příkladu kód klienta jazyka C# ví předem, že vyvolaný typ výjimky je <xref:System.String?displayProperty=nameWithType> . Vlastnost můžete přetypovat <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> zpět na původní typ, pokud je tento typ přístupný z vašeho kódu.  
  
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
- [Výjimky a zpracování výjimek](./index.md)
