---
title: 'Postupy: Zachycení výjimky nekompatibilní se specifikací CLS'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5647fc8501afe2a4bf74739fd8efd4e6b74559a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-catch-a-non-cls-exception"></a>Postupy: Zachycení výjimky nekompatibilní se specifikací CLS
Některé jazyky rozhraní .NET, včetně C + +/ CLI, povolit objekty k vyvolání výjimky, které není odvozena od <xref:System.Exception>. Takové výjimky, se nazývají *-specifikací CLS výjimky* nebo *bez výjimky*. V jazyce Visual C# můžete nelze vyvolat-specifikací CLS výjimky, ale můžete je zachytit dvěma způsoby:  
  
-   V rámci `catch (Exception e)` blokovat jako <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
     Ve výchozím nastavení sestavení Visual C# zachytí výjimky specifikací CLS jako zabalené výjimky. Tuto metodu použijte, pokud budete potřebovat přístup k původní výjimka, která je přístupná prostřednictvím <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> vlastnost. Postupem uvedeným v tomto tématu vysvětluje, jak zachytit výjimky tímto způsobem.  
  
-   V rámci bloku catch obecné (bloku catch bez zadán typ výjimky), který je put po `catch (Exception)` nebo `catch (Exception e)` bloku.  
  
     Tuto metodu použijte, pokud chcete provést některé akce (například zápis do souboru protokolu) v reakci na-specifikací CLS výjimky a nepotřebujete přístup k informacím o výjimce. Ve výchozím nastavení modul common language runtime zabalí všechny výjimky. Chcete-li toto chování zakázat, přidejte tento atribut úrovně sestavení do kódu, obvykle v souboru AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.  
  
### <a name="to-catch-a-non-cls-exception"></a>K zachycení výjimky specifikací CLS  
  
1.  V rámci `catch(Exception e) block`, použijte `as` – klíčové slovo k testování zda `e` lze převést na <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.  
  
2.  Přístup k původní výjimka pomocí <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zachytit-specifikací CLS výjimka, která byla vydána z knihovny tříd napsané v jazyce C + +/ CLR. Všimněte si, že v tomto příkladu kód klienta Visual C# vědět předem, že je typ výjimky, které jsou hlášeny <xref:System.String?displayProperty=nameWithType>. Můžete převést <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> vlastnost zpět jeho původní typ tak dlouho, dokud tento typ je přístupný z vašeho kódu.  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [Výjimky a jejich zpracování](../../../csharp/programming-guide/exceptions/index.md)
