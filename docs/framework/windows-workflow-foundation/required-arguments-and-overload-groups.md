---
title: Povinné argumenty a skupiny přetížení
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 4eb62306f52b8ff890d5a5333c3789bd84ad7f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142937"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="bc259-102">Povinné argumenty a skupiny přetížení</span><span class="sxs-lookup"><span data-stu-id="bc259-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="bc259-103">Aktivity lze nakonfigurovat tak, aby určité argumenty musí být vázány na aktivitu, která má být platná pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="bc259-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="bc259-104">Atribut `RequiredArgument` se používá k označení, že některé argumenty `OverloadGroup` na aktivitu jsou požadovány a atribut se používá k seskupení kategorií požadovaných argumentů dohromady.</span><span class="sxs-lookup"><span data-stu-id="bc259-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="bc259-105">Pomocí atributů mohou autoři aktivity poskytovat jednoduché nebo složité konfigurace ověření aktivity.</span><span class="sxs-lookup"><span data-stu-id="bc259-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="bc259-106">Použití požadovaných argumentů</span><span class="sxs-lookup"><span data-stu-id="bc259-106">Using Required Arguments</span></span>  
 <span data-ttu-id="bc259-107">Chcete-li `RequiredArgument` použít atribut v aktivitě, <xref:System.Activities.RequiredArgumentAttribute>označte požadované argumenty pomocí .</span><span class="sxs-lookup"><span data-stu-id="bc259-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="bc259-108">V tomto příkladu je definována aktivita, `Add` která má dva požadované argumenty.</span><span class="sxs-lookup"><span data-stu-id="bc259-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="bc259-109">V XAML jsou požadované argumenty také <xref:System.Activities.RequiredArgumentAttribute>indikovány pomocí .</span><span class="sxs-lookup"><span data-stu-id="bc259-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="bc259-110">V tomto `Add` příkladu je aktivita definována <xref:System.Activities.Statements.Assign%601> pomocí tří argumentů a používá aktivitu k provedení operace přidání.</span><span class="sxs-lookup"><span data-stu-id="bc259-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 <span data-ttu-id="bc259-111">Pokud je aktivita použita a některý z požadovaných argumentů není vázán, je vrácena následující chyba ověření.</span><span class="sxs-lookup"><span data-stu-id="bc259-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="bc259-112">**Hodnota pro argument požadované aktivity Operand1 nebyla zadána.**</span><span class="sxs-lookup"><span data-stu-id="bc259-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="bc259-113">Další informace o kontrole a zpracování chyb a upozornění ověření ověření naleznete [v tématu Vyvolání ověření aktivity](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="bc259-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="bc259-114">Použití skupin přetížení</span><span class="sxs-lookup"><span data-stu-id="bc259-114">Using Overload Groups</span></span>

<span data-ttu-id="bc259-115">Skupiny přetížení poskytují metodu pro označení, které kombinace argumentů jsou platné v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="bc259-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="bc259-116">Argumenty jsou seskupeny <xref:System.Activities.OverloadGroupAttribute>pomocí .</span><span class="sxs-lookup"><span data-stu-id="bc259-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="bc259-117">Každá skupina má název, který <xref:System.Activities.OverloadGroupAttribute>je určen .</span><span class="sxs-lookup"><span data-stu-id="bc259-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="bc259-118">Aktivita je platná, pokud jsou vázány pouze jedna sada argumentů ve skupině přetížení.</span><span class="sxs-lookup"><span data-stu-id="bc259-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="bc259-119">V následujícím příkladu `CreateLocation` je definována třída.</span><span class="sxs-lookup"><span data-stu-id="bc259-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }
}  
```  
  
 <span data-ttu-id="bc259-120">Cílem této činnosti je určit umístění v USA.</span><span class="sxs-lookup"><span data-stu-id="bc259-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="bc259-121">Chcete-li to provést, uživatel aktivity můžete zadat umístění pomocí jedné ze tří skupin argumentů.</span><span class="sxs-lookup"><span data-stu-id="bc259-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="bc259-122">Chcete-li zadat platné kombinace argumentů, jsou definovány tři skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="bc259-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="bc259-123">`G1`obsahuje `Latitude` argumenty a. `Longitude`</span><span class="sxs-lookup"><span data-stu-id="bc259-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="bc259-124">`G2`obsahuje `Street` `City`, `State`a .</span><span class="sxs-lookup"><span data-stu-id="bc259-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="bc259-125">`G3`obsahuje `Street` `Zip`a .</span><span class="sxs-lookup"><span data-stu-id="bc259-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="bc259-126">`Name`je také povinný argument, ale není součástí skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="bc259-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="bc259-127">Aby byla tato aktivita platná, `Name` musela by být spojena se všemi argumenty z jedné a pouze jedné skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="bc259-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="bc259-128">V následujícím příkladu převzaty z access [aktivity databáze](./samples/database-access-activities.md) `ConnectionString` ukázky existují dvě skupiny přetížení: a `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="bc259-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="bc259-129">Aby byla tato aktivita `ProviderName` platná, musí být argumenty a `ConnectionString` vázány nebo `ConfigName` argument, nikoli však oba.</span><span class="sxs-lookup"><span data-stu-id="bc259-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```csharp  
public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }
}  
```  
  
 <span data-ttu-id="bc259-130">Při definování skupiny přetížení:</span><span class="sxs-lookup"><span data-stu-id="bc259-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="bc259-131">Skupina přetížení nemůže být podmnožinou nebo ekvivalentní sadou jiné skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="bc259-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bc259-132">Existuje jedna výjimka z tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="bc259-132">There is one exception to this rule.</span></span> <span data-ttu-id="bc259-133">Pokud skupina přetížení je podmnožinou jiné skupiny přetížení a `RequiredArgument` podmnožina obsahuje pouze argumenty, kde je `false`, pak skupina přetížení je platný.</span><span class="sxs-lookup"><span data-stu-id="bc259-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="bc259-134">Přetížení skupiny mohou překrývat, ale je chyba, pokud průsečík skupin obsahuje všechny požadované argumenty jedné nebo obou skupin přetížení.</span><span class="sxs-lookup"><span data-stu-id="bc259-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="bc259-135">V předchozím `G2` příkladu `G3` se překrývaly skupiny přetížení a skupiny přetížení, ale protože průsečík neobsahoval všechny argumenty jedné nebo obou skupin, byl tento počet platný.</span><span class="sxs-lookup"><span data-stu-id="bc259-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="bc259-136">Při vazby argumenty ve skupině přetížení:</span><span class="sxs-lookup"><span data-stu-id="bc259-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="bc259-137">Skupina přetížení je považována za `RequiredArgument` vázanou, pokud jsou všechny argumenty ve skupině vázány.</span><span class="sxs-lookup"><span data-stu-id="bc259-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="bc259-138">Pokud skupina má `RequiredArgument` nulové argumenty a alespoň jeden argument vázán, pak je skupina považována za vázanou.</span><span class="sxs-lookup"><span data-stu-id="bc259-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="bc259-139">Je chyba ověření, pokud jsou vázány žádné skupiny přetížení, pokud jedna skupina přetížení nemá žádné `RequiredArgument` argumenty v něm.</span><span class="sxs-lookup"><span data-stu-id="bc259-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="bc259-140">Je chyba mít více než jednu skupinu přetížení vázána, to znamená, že všechny požadované argumenty v jedné skupině přetížení jsou vázány a jakýkoli argument v jiné skupině přetížení je také vázán.</span><span class="sxs-lookup"><span data-stu-id="bc259-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
