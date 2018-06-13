---
title: 'Postupy: vytváření podepsaných přátelských sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 34243a65f57f41c358439baac82a1ce169233259
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340655"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="0eb88-102">Postupy: vytváření podepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="0eb88-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="0eb88-103">Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které mají silné názvy.</span><span class="sxs-lookup"><span data-stu-id="0eb88-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="0eb88-104">Obě sestavení musí mít silné názvy.</span><span class="sxs-lookup"><span data-stu-id="0eb88-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="0eb88-105">I když obě sestavení v tomto příkladu používat stejné klíče, můžete použít různé klíče pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="0eb88-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="0eb88-106">Chcete-li vytvořit podepsané sestavení a přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="0eb88-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="0eb88-107">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="0eb88-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="0eb88-108">Generování keyfile a zobrazit svůj veřejný klíč, použijte následující sekvence příkazů pomocí nástroje silného názvu.</span><span class="sxs-lookup"><span data-stu-id="0eb88-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="0eb88-109">Další informace najdete v tématu [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="0eb88-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="0eb88-110">Vygenerovat klíč silné jméno – v tomto příkladu a uložit ho do souboru FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="0eb88-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="0eb88-111">Extrahování veřejný klíč z FriendAssemblies.snk a umístí jej do FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="0eb88-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="0eb88-112">Zobrazí veřejný klíč uložený v souboru FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="0eb88-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="0eb88-113">Vytvoření souboru C# s názvem `friend_signed_A` obsahující následující kód.</span><span class="sxs-lookup"><span data-stu-id="0eb88-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="0eb88-114">Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.</span><span class="sxs-lookup"><span data-stu-id="0eb88-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="0eb88-115">Nástroje pro silný název generuje nový veřejný klíč pokaždé, když ji spustí.</span><span class="sxs-lookup"><span data-stu-id="0eb88-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="0eb88-116">Proto je potřeba nahradit veřejný klíč v následujícím kódu veřejný klíč, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0eb88-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="0eb88-117">Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="0eb88-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="0eb88-118">Vytvoření souboru C#, který je pojmenován `friend_signed_B` a obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="0eb88-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="0eb88-119">Protože friend_signed_A určuje friend_signed_B jako přátelského sestavení, můžete přístup k kód v friend_signed_B `internal` typy a členy z friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="0eb88-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="0eb88-120">Soubor obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="0eb88-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="0eb88-121">Kompilace a friend_signed_B se přihlaste pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="0eb88-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="0eb88-122">Název sestavení generované kompilátorem musí odpovídat názvu sestavení friend předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0eb88-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="0eb88-123">Musíte explicitně zadat název výstupu sestavení (.exe nebo .dll) pomocí `/out` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0eb88-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="0eb88-124">Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="0eb88-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="0eb88-125">Spusťte soubor friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="0eb88-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="0eb88-126">Program vytiskne řetězec "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="0eb88-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0eb88-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0eb88-127">.NET Framework Security</span></span>  
 <span data-ttu-id="0eb88-128">Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="0eb88-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="0eb88-129">Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `internal` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="0eb88-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb88-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="0eb88-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="0eb88-131">Sestavení a globální mezipaměti sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="0eb88-131">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="0eb88-132">Přátelská sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="0eb88-132">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="0eb88-133">Postupy: vytváření nepodepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="0eb88-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="0eb88-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="0eb88-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="0eb88-135">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="0eb88-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="0eb88-136">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="0eb88-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="0eb88-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0eb88-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
