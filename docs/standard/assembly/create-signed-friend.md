---
title: 'Postup: Vytvoření podepsaných sestavení přátel'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159491"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="2490e-102">Postup: Vytvoření podepsaných sestavení přátel</span><span class="sxs-lookup"><span data-stu-id="2490e-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="2490e-103">Tento příklad ukazuje, jak používat sestavení přátel s sestaveními, které mají silné názvy.</span><span class="sxs-lookup"><span data-stu-id="2490e-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="2490e-104">Obě sestavení musí být silné pojmenované.</span><span class="sxs-lookup"><span data-stu-id="2490e-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="2490e-105">Přestože obě sestavení v tomto příkladu používají stejné klíče, můžete použít různé klíče pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="2490e-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="2490e-106">Vytvoření podepsaného sestavení a sestavy přítele</span><span class="sxs-lookup"><span data-stu-id="2490e-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="2490e-107">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="2490e-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="2490e-108">Pomocí následující posloupnosti příkazů s nástrojem Silný název vygenerujte soubor kláves a zobrazte jeho veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="2490e-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="2490e-109">Další informace naleznete v [tématu Sn.exe (nástroj silný název).](../../framework/tools/sn-exe-strong-name-tool.md)</span><span class="sxs-lookup"><span data-stu-id="2490e-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="2490e-110">Vygenerujte klíč silného názvu pro tento příklad a uložte jej do souboru *FriendAssemblies.snk*:</span><span class="sxs-lookup"><span data-stu-id="2490e-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="2490e-111">Extrahujte veřejný klíč z *FriendAssemblies.snk* a vložte jej do *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="2490e-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="2490e-112">Zobrazí veřejný klíč uložený v souboru *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="2490e-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="2490e-113">Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_signed_A,* který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="2490e-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="2490e-114">Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat *friend_signed_B* jako sestavení přítele.</span><span class="sxs-lookup"><span data-stu-id="2490e-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="2490e-115">Nástroj Silný název vygeneruje nový veřejný klíč při každém spuštění.</span><span class="sxs-lookup"><span data-stu-id="2490e-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="2490e-116">Proto je nutné nahradit veřejný klíč v následujícím kódu veřejným klíčem, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2490e-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="2490e-117">Kompilujte a podepište *friend_signed_A* pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="2490e-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="2490e-118">Vytvořte soubor jazyka C# nebo Visual Basic s názvem *friend_signed_B,* který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="2490e-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="2490e-119">Vzhledem k tomu, *že friend_signed_A* určuje *friend_signed_B* `internal` jako sestavení přítele, kód v *friend_signed_B* může přistupovat (C#) nebo `Friend` (Visual Basic) typy a členy z *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="2490e-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="2490e-120">Soubor obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="2490e-120">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="2490e-121">Kompilace a podepisování *friend_signed_B* pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="2490e-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="2490e-122">Název sestavení generovanékompilátorem musí odpovídat názvu sestavení friend <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> předaném atributu.</span><span class="sxs-lookup"><span data-stu-id="2490e-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="2490e-123">Je nutné explicitně zadat název výstupního sestavení (*.exe* `-out` nebo *.dll*) pomocí možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2490e-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="2490e-124">Další informace naleznete [v tématu -out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="2490e-124">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="2490e-125">Spusťte soubor *friend_signed_B.exe.*</span><span class="sxs-lookup"><span data-stu-id="2490e-125">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="2490e-126">Program vyveze řetězec **Class1.Test**.</span><span class="sxs-lookup"><span data-stu-id="2490e-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="2490e-127">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="2490e-127">.NET security</span></span>  
 <span data-ttu-id="2490e-128">Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributem <xref:System.Security.Permissions.StrongNameIdentityPermission> a třídou.</span><span class="sxs-lookup"><span data-stu-id="2490e-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="2490e-129">Hlavní <xref:System.Security.Permissions.StrongNameIdentityPermission> rozdíl je, že můžete požadovat oprávnění zabezpečení ke spuštění <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> určité části kódu, zatímco atribut řídí viditelnost `internal` (C#) nebo `Friend` (Visual Basic) typy a členy.</span><span class="sxs-lookup"><span data-stu-id="2490e-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2490e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2490e-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="2490e-131">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="2490e-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="2490e-132">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="2490e-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="2490e-133">Postup: Vytvoření nepodepsaných sestavení přátel</span><span class="sxs-lookup"><span data-stu-id="2490e-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="2490e-134">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="2490e-134">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="2490e-135">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2490e-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="2490e-136">Sn.exe (nástroj silný název)</span><span class="sxs-lookup"><span data-stu-id="2490e-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="2490e-137">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="2490e-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="2490e-138">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2490e-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2490e-139">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2490e-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
