---
title: Přátelská sestavení (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: e8c295fe23685e39e20a14ff23139339f24564c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510082"
---
# <a name="friend-assemblies-c"></a>Přátelská sestavení (C#)
A *sestavení typu friend* je sestavení, které můžou přistupovat k jiné sestavení [interní](../../../../csharp/language-reference/keywords/internal.md) typy a členy. Pokud identifikujete sestavení jako sestavení typu friend, máte již označit typy a členy jako veřejné je přístupná pomocí jiné sestavení. To je zvlášť vhodné v následujících scénářích:  
  
-   Během testování částí, pokud testovací kód je spuštěn samostatné sestavení ale vyžaduje přístupu ke členům v sestavení, testování, které jsou označeny jako `internal` .  
  
-   Když vyvíjíte knihovny tříd a dodatky ke knihovně jsou obsaženy v samostatné sestavení, ale vyžadují přístup ke členům v existující sestavení, které jsou označeny jako `internal` .  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut k identifikaci přátelských sestavení pro dané sestavení. V následujícím příkladu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut v sestavení A a určuje sestavení `AssemblyB` jako sestavení typu friend. To umožňuje sestavení `AssemblyB` přístup ke všem typy a členy v sestavení, které jsou označeny jako `internal`.  
  
> [!NOTE]
>  Pokud kompilujete sestavení (sestavení `AssemblyB`), které budou přistupovat k interní typy nebo interní členy jiné sestavení (sestavení *A*), musíte explicitně zadat název výstupního souboru (.exe nebo .dll) s použitím **/out** – možnost kompilátoru. To je požadované, protože kompilátor nebyl zatím nevygenerovaly název sestavení, ve kterém je sestavení v době, kdy je vytvoření vazby na externí odkazy. Další informace najdete v tématu [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .  
  
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
  
 Pouze sestavení, která explicitně zadáte jako přátelé dostanete `internal` typy a členy. Například, pokud sestavení B je přátelská sestavení A a sestavení C odkazy na sestavení B, C nemá přístup k `internal` typy v A.  
  
 Kompilátor provádí nějaké základní ověření předat název sestavení typu friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut. Pokud sestavení *A* deklaruje *B* jako sestavení typu friend, ověřovacích pravidel jsou následující:  
  
-   Pokud sestavení *A* je silný název sestavení *B* musí také být silný název. Název sestavení typu friend, který je předán atributu musí obsahovat název sestavení a veřejný klíč, který se používá k podepsání sestavení silným názvem klíče *B*.  
  
     Název sestavení typu friend, který je předán <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut nemůže být silný název sestavení *B*: nezahrnují sestavení verze, jazykovou verzi, architektury nebo token veřejného klíče.  
  
-   Pokud sestavení *A* není silným názvem, název sestavení typu friend musí obsahovat pouze název sestavení. Další informace najdete v tématu [postupy: vytváření nepodepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Pokud sestavení *B* je silným názvem, je nutné zadat klíče silného názvu pro sestavení *B* pomocí nastavení projektu nebo příkazového řádku `/keyfile` – možnost kompilátoru. Další informace najdete v tématu [postupy: vytvoření podepsané přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Třída rovněž poskytuje možnost sdílení typů, s těmito rozdíly:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> platí pro určitého typu, zatímco sestavení typu friend se vztahuje na celé sestavení.  
  
-   Pokud existují stovky typy v sestavení *A* , kterou chcete sdílet s sestavení *B*, budete muset přidat <xref:System.Security.Permissions.StrongNameIdentityPermission> pro všechny z nich. Pokud používáte spřátelené sestavení, stačí jednou deklarace typu friend vztah.  
  
-   Pokud používáte <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, které chcete sdílet musí být deklarován jako veřejná. Pokud používáte spřátelené sestavení, sdílené typy jsou deklarovány jako `internal`.  
  
 Informace o tom, jak získat přístup k sestavení `internal` typy a metody ze soubor modulu (soubor s příponou .netmodule), najdete v části [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
- <xref:System.Security.Permissions.StrongNameIdentityPermission>  
- [Postupy: vytváření nepodepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
- [Postupy: vytváření podepsaných přátelských sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
- [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)
