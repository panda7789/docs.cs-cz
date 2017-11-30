---
title: "Přátelská sestavení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 20b8d4f2d58af510a28160d28e6ef740d293d835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assemblies-c"></a>Přátelská sestavení (C#)
A *přátelského sestavení* je sestavení, které můžete přístup k jiné sestavení [interní](../../../../csharp/language-reference/keywords/internal.md) typy a členy. Pokud identifikovat sestavení jako přátelského sestavení, již není k označení typy a členy jako veřejné, aby k nim přístup ostatních sestavení. To je zvlášť vhodné v následujících scénářích:  
  
-   Během testování částí, při spuštění testovacího kódu v samostatné sestavení, ale vyžaduje přístupu ke členům v sestavení testuje, které jsou označeny jako `internal` .  
  
-   Pokud vyvíjíte knihovny tříd a přidané do knihovny jsou obsaženy v samostatné sestavení, ale vyžadují přístup ke členům v existujících sestavení, které jsou označeny jako `internal` .  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k identifikaci jeden nebo více sestavení, přítele pro zadaného sestavení. Následující příklad používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> v sestavení A a určuje sestavení `AssemblyB` jako přátelského sestavení. Díky tomu sestavení `AssemblyB` přístup ke všem typy a členy v sestavení, které jsou označeny jako `internal`.  
  
> [!NOTE]
>  Při kompilaci sestavení (sestavení `AssemblyB`), bude přístup k interní typy nebo interní členy jiné sestavení (sestavení *A*), musíte explicitně zadat název výstupního souboru (.exe nebo .dll) pomocí **/out** – možnost kompilátoru. To je potřeba, protože kompilátor ještě nebyl vygenerován název sestavení, ve kterém je sestavení v době, kdy je vytvoření vazby na externí odkazy. Další informace najdete v tématu [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .  
  
```csharp  
using System.Runtime.CompilerServices;  
using System;  
  
[assembly: InternalsVisibleTo("AssemblyB")]  
  
// The class is internal by default.  
class FriendClass  
{  
    public void Test()  
    {  
        Console.WriteLine("Sample Class");  
    }  
}  
  
// Public class that has an internal method.  
public class ClassWithFriendMethod  
{  
    internal void Test()  
    {  
        Console.WriteLine("Sample Method");  
    }  
  
}  
```  
  
 Pouze sestavení, která explicitně zadáte jako přístup přátel `internal` typy a členy. Například pokud je sestavení B přátelských sestavení A a sestavení C odkazy na sestavení B, C nemá přístup k `internal` typy v A.  
  
 Kompilátor provádí základní ověření předaný název sestavení friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Pokud sestavení *A* deklaruje *B* jako přátelského sestavení ověřovacích pravidel jsou následující:  
  
-   Pokud sestavení *A* se silným názvem, sestavení *B* musí také mít silné název. Název sestavení friend, který je předán do atribut musí obsahovat název sestavení a veřejného klíče pro silné jméno – klíč, který se používá k podepsání sestavení *B*.  
  
     Název sestavení friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemůže být silného názvu sestavení *B*: nezahrnují verze sestavení, jazykovou verzi, architektury nebo tokenu veřejného klíče.  
  
-   Pokud sestavení *A* není silné s názvem, přítele název sestavení by měla obsahovat jenom název sestavení. Další informace najdete v tématu [postupy: vytváření nepodepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Pokud sestavení *B* je silné s názvem, je nutné zadat silné jméno – klíč pro sestavení *B* pomocí nastavení projektu nebo příkazového řádku `/keyfile` – možnost kompilátoru. Další informace najdete v tématu [postupy: vytvoření podepsané přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Třída rovněž poskytuje možnost sdílet typy, s následující rozdíly:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission>platí pro typ jednotlivých během přátelského sestavení celá sestava.  
  
-   Pokud se používají stovky typy v sestavení *A* , kterou chcete sdílet s sestavení *B*, budete muset přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> ke všem z nich. Pokud používáte přátelského sestavení, musíte pouze deklarovat vztah friend jednou.  
  
-   Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet muset být deklarována jako veřejné. Pokud používáte přátelského sestavení, sdílené typy jsou deklarovány jako `internal`.  
  
 Informace o tom, jak přistupovat sestavení `internal` typy a metody ze souboru modulu (soubor s příponou .netmodule), najdete v části [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [Postupy: vytváření nepodepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [Postupy: vytváření podepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Průvodce programováním v C#](../../../../csharp/programming-guide/index.md)
