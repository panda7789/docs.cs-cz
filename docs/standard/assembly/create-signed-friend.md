---
title: 'Postupy: Vytváření podepsaných přátelských sestavení'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159491"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="959a9-102">Postupy: Vytváření podepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="959a9-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="959a9-103">Tento příklad ukazuje, jak použít sestavení typu Friend se sestaveními, která mají silné názvy.</span><span class="sxs-lookup"><span data-stu-id="959a9-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="959a9-104">Obě sestavení musí mít silný název.</span><span class="sxs-lookup"><span data-stu-id="959a9-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="959a9-105">I když obě sestavení v tomto příkladu používají stejné klíče, můžete použít různé klíče pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="959a9-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="959a9-106">Vytvořit podepsané sestavení a sestavení typu Friend</span><span class="sxs-lookup"><span data-stu-id="959a9-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="959a9-107">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="959a9-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="959a9-108">Použijte následující posloupnost příkazů s nástrojem silného názvu k vygenerování souboru klíče a k zobrazení jeho veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="959a9-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="959a9-109">Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="959a9-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="959a9-110">Vygenerujte klíč se silným názvem pro tento příklad a uložte ho do souboru *FriendAssemblies. snk*:</span><span class="sxs-lookup"><span data-stu-id="959a9-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="959a9-111">Extrahujte veřejný klíč z *FriendAssemblies. snk* a vložte ho do *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="959a9-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="959a9-112">Zobrazit veřejný klíč uložený v souboru *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="959a9-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="959a9-113">Vytvořte soubor C# nebo Visual Basic s názvem *friend_signed_A* , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="959a9-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="959a9-114">Kód používá atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> k deklaraci *friend_signed_B* jako sestavení typu Friend.</span><span class="sxs-lookup"><span data-stu-id="959a9-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="959a9-115">Nástroj silného názvu vygeneruje nový veřejný klíč při každém spuštění.</span><span class="sxs-lookup"><span data-stu-id="959a9-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="959a9-116">Proto je nutné nahradit veřejný klíč v následujícím kódu veřejným klíčem, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="959a9-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

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

4. <span data-ttu-id="959a9-117">Zkompilujte a podepište *friend_signed_A* pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="959a9-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="959a9-118">Vytvořte soubor C# nebo Visual Basic s názvem *friend_signed_B* , který obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="959a9-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="959a9-119">Vzhledem k tomu, že *friend_signed_A* Určuje *friend_signed_B* jako sestavení typu friend, kód v *friend_signed_B* můžeC#přistupovat k typům `internal` () nebo `Friend` (Visual Basic) a členům z *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="959a9-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="959a9-120">Soubor obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="959a9-120">The file contains the following code.</span></span>  

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

6. <span data-ttu-id="959a9-121">Zkompilujte a podepište *friend_signed_B* pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="959a9-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="959a9-122">Název sestavení generované kompilátorem se musí shodovat s názvem sestavení typu Friend předanému atributu <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="959a9-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="959a9-123">Musíte explicitně zadat název výstupního sestavení ( *. exe* nebo *. dll*) pomocí možnosti kompilátoru `-out`.</span><span class="sxs-lookup"><span data-stu-id="959a9-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="959a9-124">Další informace naleznete v tématu [-out (C# možnosti kompilátoru)](../../csharp/language-reference/compiler-options/out-compiler-option.md) nebo [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="959a9-124">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="959a9-125">Spusťte soubor *friend_signed_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="959a9-125">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="959a9-126">Program vytvoří výstup řetězce **Class1. test**.</span><span class="sxs-lookup"><span data-stu-id="959a9-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="959a9-127">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="959a9-127">.NET security</span></span>  
 <span data-ttu-id="959a9-128">Existují podobnosti mezi atributem <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> a třídou <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="959a9-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="959a9-129">Hlavním rozdílem je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> může vyžadovat oprávnění zabezpečení ke spuštění konkrétní části kódu, zatímco atribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> řídí viditelnost typů a členů `internal` (C#) nebo `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="959a9-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="959a9-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="959a9-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="959a9-131">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="959a9-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="959a9-132">Friend – sestavení</span><span class="sxs-lookup"><span data-stu-id="959a9-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="959a9-133">Postupy: vytváření nepodepsaných přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="959a9-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="959a9-134">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="959a9-134">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="959a9-135">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="959a9-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="959a9-136">SN. exe (Nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="959a9-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="959a9-137">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="959a9-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="959a9-138">C#Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="959a9-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="959a9-139">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="959a9-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
