---
title: "Postupy: vytváření podepsaných přátelských sestavení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d3d9d4c549654341c0739cc8132d953623482d62
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="42e3b-102">Postupy: vytváření podepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="42e3b-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="42e3b-103">Tento příklad ukazuje způsob použití přátelských sestavení s sestavení, které mají silné názvy.</span><span class="sxs-lookup"><span data-stu-id="42e3b-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="42e3b-104">Obě sestavení musí mít silné názvy.</span><span class="sxs-lookup"><span data-stu-id="42e3b-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="42e3b-105">I když obě sestavení v tomto příkladu používat stejné klíče, můžete použít různé klíče pro dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="42e3b-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="42e3b-106">Chcete-li vytvořit podepsané sestavení a přátelských sestavení</span><span class="sxs-lookup"><span data-stu-id="42e3b-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="42e3b-107">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="42e3b-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="42e3b-108">Generování keyfile a zobrazit svůj veřejný klíč, použijte následující sekvence příkazů pomocí nástroje silného názvu.</span><span class="sxs-lookup"><span data-stu-id="42e3b-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="42e3b-109">Další informace najdete v tématu [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="42e3b-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="42e3b-110">Vygenerovat klíč silné jméno – v tomto příkladu a uložit ho do souboru FriendAssemblies.snk:</span><span class="sxs-lookup"><span data-stu-id="42e3b-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="42e3b-111">Extrahování veřejný klíč z FriendAssemblies.snk a umístí jej do FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="42e3b-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="42e3b-112">Zobrazí veřejný klíč uložený v souboru FriendAssemblies.publickey:</span><span class="sxs-lookup"><span data-stu-id="42e3b-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="42e3b-113">Vytvoření souboru C# s názvem `friend_signed_A` obsahující následující kód.</span><span class="sxs-lookup"><span data-stu-id="42e3b-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="42e3b-114">Kód používá <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut deklarovat friend_signed_B jako přátelského sestavení.</span><span class="sxs-lookup"><span data-stu-id="42e3b-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="42e3b-115">Nástroje pro silný název generuje nový veřejný klíč pokaždé, když ji spustí.</span><span class="sxs-lookup"><span data-stu-id="42e3b-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="42e3b-116">Proto je potřeba nahradit veřejný klíč v následujícím kódu veřejný klíč, který jste právě vygenerovali, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="42e3b-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="42e3b-117">Kompilace a friend_signed_A se přihlaste pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="42e3b-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="42e3b-118">Vytvoření souboru C#, který je pojmenován `friend_signed_B` a obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="42e3b-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="42e3b-119">Protože friend_signed_A určuje friend_signed_B jako přátelského sestavení, můžete přístup k kód v friend_signed_B `internal` typy a členy z friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="42e3b-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="42e3b-120">Soubor obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="42e3b-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="42e3b-121">Kompilace a friend_signed_B se přihlaste pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="42e3b-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="42e3b-122">Název sestavení generované kompilátorem musí odpovídat názvu sestavení friend předaný <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="42e3b-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="42e3b-123">Musíte explicitně zadat název výstupu sestavení (.exe nebo .dll) pomocí `/out` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="42e3b-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="42e3b-124">Další informace najdete v tématu [/out (možnosti kompilátoru C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="42e3b-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="42e3b-125">Spusťte soubor friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="42e3b-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="42e3b-126">Program vytiskne řetězec "Class1.Test".</span><span class="sxs-lookup"><span data-stu-id="42e3b-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="42e3b-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="42e3b-127">.NET Framework Security</span></span>  
 <span data-ttu-id="42e3b-128">Existují podobnosti mezi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut a <xref:System.Security.Permissions.StrongNameIdentityPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="42e3b-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="42e3b-129">Hlavní rozdíl je, že <xref:System.Security.Permissions.StrongNameIdentityPermission> oprávnění zabezpečení ke spuštění konkrétní části kódu, můžete požadovat, zatímco <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atribut určuje, zda se `internal` typy a členy.</span><span class="sxs-lookup"><span data-stu-id="42e3b-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e3b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="42e3b-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="42e3b-131">Sestavení a globální mezipaměti sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="42e3b-131">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="42e3b-132">Přátelská sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="42e3b-132">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="42e3b-133">Postupy: vytváření nepodepsaných přátelských sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="42e3b-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="42e3b-134">/ keyfile</span><span class="sxs-lookup"><span data-stu-id="42e3b-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="42e3b-135">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="42e3b-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="42e3b-136">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="42e3b-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="42e3b-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="42e3b-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
