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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd6f14f89d143edd03f8b5d028ec84315b2f2e97
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "44756324"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Postupy: Načtení sestavení do domény aplikace
Existuje několik způsobů, jak načíst sestavení do domény aplikace. Doporučeným způsobem je použít `static` (`Shared` v jazyce Visual Basic) <xref:System.Reflection.Assembly.Load%2A> metodu <xref:System.Reflection.Assembly?displayProperty=nameWithType> třídy. Další způsoby, které lze načíst sestavení patří:  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> Metodu <xref:System.Reflection.Assembly> třídy načte sestavení zadané umístění souboru. Načtení sestavení se tato metoda používá různé zatížení kontext.  
  
-   <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> a <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> metody načtení sestavení do kontextu pouze pro reflexi. Sestavení zavedených v tomto kontextu můžete prověřit, ale nebyl proveden, umožňující zkoumání sestavení, které se zaměřují na jiných platformách. Zobrazit [postupy: načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
>  Kontextu pouze pro reflexi je v rozhraní .NET Framework verze 2.0 nová.  
  
-   Metody jako <xref:System.AppDomain.CreateInstance%2A> a <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> z <xref:System.AppDomain> třídy lze načíst sestavení do domény aplikace.  
  
-   <xref:System.Type.GetType%2A> Metodu <xref:System.Type> třídy lze načíst sestavení.  
  
-   <xref:System.AppDomain.Load%2A> Metodu <xref:System.AppDomain?displayProperty=nameWithType> třídy lze načíst sestavení, ale používá se především pro interoperabilitu COM. Není vhodné používat k načtení sestavení do domény aplikace, ze kterého se označuje jako domény aplikace.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework verze 2.0, nenačte modul runtime, který byl zkompilován s verzí rozhraní .NET Framework, která má vyšší číslo verze než aktuálně zavedený modul runtime sestavení. To platí pro kombinaci hlavní a vedlejší součásti číslo verze.  
  
 Můžete zadat tak, jak just-in-time (JIT) kompilaci kódu z načtených sestavení jsou sdílena mezi doménami aplikace. Další informace najdete v tématu [doménám a sestavením aplikací](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).  
  
## <a name="example"></a>Příklad  
 Následující kód načte sestavení do aktuální domény aplikace s názvem "example.exe" nebo "example.dll" získá typ s názvem `Example` ze sestavení, získá konstruktor bez parametrů metodu s názvem `MethodA` u tohoto typu a provede metodu. Úplné informace o získání informací z načtené sestavení, naleznete v tématu [dynamické načtení a použití typů](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 [Programování pomocí domén aplikace](application-domains.md#programming-with-application-domains)  
 [Reflexe](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Používání domén aplikací](../../../docs/framework/app-domains/use.md)  
 [Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
 [Domény a sestavení aplikací](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
