---
title: Povinné argumenty a skupiny přetížení
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 5249cbb127064ffa5023074481a47decad279128
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964915"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="12d40-102">Povinné argumenty a skupiny přetížení</span><span class="sxs-lookup"><span data-stu-id="12d40-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="12d40-103">Aktivity lze nakonfigurovat tak, aby byly určité argumenty vázány na to, aby byla aktivita platná pro provedení.</span><span class="sxs-lookup"><span data-stu-id="12d40-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="12d40-104">Atribut slouží k označení, že jsou požadovány určité argumenty aktivity `OverloadGroup` , a atribut je použit k seskupení kategorií požadovaných argumentů společně. `RequiredArgument`</span><span class="sxs-lookup"><span data-stu-id="12d40-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="12d40-105">Pomocí atributů můžou autoři aktivity poskytovat jednoduché nebo složité konfigurace ověřování aktivit.</span><span class="sxs-lookup"><span data-stu-id="12d40-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="12d40-106">Použití požadovaných argumentů</span><span class="sxs-lookup"><span data-stu-id="12d40-106">Using Required Arguments</span></span>  
 <span data-ttu-id="12d40-107">Chcete-li `RequiredArgument` použít atribut v aktivitě, určete požadované argumenty pomocí <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="12d40-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="12d40-108">V tomto příkladu `Add` je definována aktivita, která má dva povinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="12d40-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="12d40-109">V jazyce XAML jsou povinné argumenty také označeny pomocí <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="12d40-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="12d40-110">V tomto příkladu `Add` je aktivita definovaná pomocí tří argumentů a k provedení operace přidání <xref:System.Activities.Statements.Assign%601> používá aktivitu.</span><span class="sxs-lookup"><span data-stu-id="12d40-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="12d40-111">Pokud se aktivita používá a některý z požadovaných argumentů není vázaný na, vrátí se následující chyba ověřování.</span><span class="sxs-lookup"><span data-stu-id="12d40-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="12d40-112">**Nebyla zadána hodnota pro argument požadované aktivity ' Operand1 '.**</span><span class="sxs-lookup"><span data-stu-id="12d40-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="12d40-113">Další informace o kontrole a zpracování chyb a upozornění ověřování najdete v tématu [vyvolání ověření aktivity](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="12d40-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="12d40-114">Použití skupin přetížení</span><span class="sxs-lookup"><span data-stu-id="12d40-114">Using Overload Groups</span></span>

<span data-ttu-id="12d40-115">Přetížené skupiny poskytují metodu pro indikaci, které kombinace argumentů jsou v aktivitě platné.</span><span class="sxs-lookup"><span data-stu-id="12d40-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="12d40-116">Argumenty jsou seskupené dohromady pomocí <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="12d40-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="12d40-117">Každé skupině se předává název, který je určen v <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="12d40-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="12d40-118">Tato aktivita je platná, pokud je svázána pouze jedna sada argumentů v přetížené skupině.</span><span class="sxs-lookup"><span data-stu-id="12d40-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="12d40-119">V následujícím příkladu `CreateLocation` je definována třída.</span><span class="sxs-lookup"><span data-stu-id="12d40-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="12d40-120">Cílem této aktivity je určit umístění v USA.</span><span class="sxs-lookup"><span data-stu-id="12d40-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="12d40-121">Za tímto účelem může uživatel aktivity určit umístění pomocí jedné ze tří skupin argumentů.</span><span class="sxs-lookup"><span data-stu-id="12d40-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="12d40-122">Chcete-li určit platnou kombinaci argumentů, jsou definovány tři přetížené skupiny.</span><span class="sxs-lookup"><span data-stu-id="12d40-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="12d40-123">`G1`obsahuje argumenty `Longitude`a. `Latitude`</span><span class="sxs-lookup"><span data-stu-id="12d40-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="12d40-124">`G2`obsahuje `Street`, `City`, a `State`.</span><span class="sxs-lookup"><span data-stu-id="12d40-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="12d40-125">`G3`obsahuje `Street` a `Zip`.</span><span class="sxs-lookup"><span data-stu-id="12d40-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="12d40-126">`Name`je také povinný argument, ale není součástí přetížené skupiny.</span><span class="sxs-lookup"><span data-stu-id="12d40-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="12d40-127">Aby byla tato aktivita platná, `Name` musí být vázána společně se všemi argumenty z jedné a pouze jedné přetížené skupiny.</span><span class="sxs-lookup"><span data-stu-id="12d40-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="12d40-128">V následujícím příkladu pořízených z ukázky [aktivity přístupu k databázi](./samples/database-access-activities.md) existují dvě přetížené skupiny: `ConnectionString` a. `ConfigFileSectionName`</span><span class="sxs-lookup"><span data-stu-id="12d40-128">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="12d40-129">Aby byla tato aktivita platná, musí `ProviderName` `ConfigName` být argumenty a `ConnectionString` buď vázané, nebo argument, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="12d40-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```  
Public class DbUpdate: AsyncCodeActivity  
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
  
 <span data-ttu-id="12d40-130">Při definování přetížené skupiny:</span><span class="sxs-lookup"><span data-stu-id="12d40-130">When defining an overload group:</span></span>  
  
- <span data-ttu-id="12d40-131">Přetížená skupina nemůže být podmnožinou nebo ekvivalentní sadou jiné přetížené skupiny.</span><span class="sxs-lookup"><span data-stu-id="12d40-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="12d40-132">Toto pravidlo obsahuje jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="12d40-132">There is one exception to this rule.</span></span> <span data-ttu-id="12d40-133">Pokud je přetížená skupina podmnožinou jiné přetížené skupiny a podmnožina obsahuje pouze argumenty `RequiredArgument` , `false`kde je, je přetížená skupina platná.</span><span class="sxs-lookup"><span data-stu-id="12d40-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="12d40-134">Přetížené skupiny se mohou překrývat, ale jedná se o chybu, pokud průnik skupin obsahuje všechny požadované argumenty jedné nebo obou skupin přetížení.</span><span class="sxs-lookup"><span data-stu-id="12d40-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="12d40-135">V předchozím příkladu se `G2` překrývají skupiny a `G3` přetížení, ale vzhledem k tomu, že průnik neobsahoval všechny argumenty jedné nebo obou skupin, které byly platné.</span><span class="sxs-lookup"><span data-stu-id="12d40-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="12d40-136">Při vazbách argumentů v přetížené skupině:</span><span class="sxs-lookup"><span data-stu-id="12d40-136">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="12d40-137">Přetížená skupina se považuje za vázanou, `RequiredArgument` Pokud jsou všechny argumenty ve skupině svázané.</span><span class="sxs-lookup"><span data-stu-id="12d40-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="12d40-138">Pokud má skupina nulové `RequiredArgument` argumenty a alespoň jeden argument je vázaný, bude skupina považována za vázanou.</span><span class="sxs-lookup"><span data-stu-id="12d40-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="12d40-139">Jedná se o chybu ověřování, pokud nejsou svázány žádné přetížené skupiny, pokud v `RequiredArgument` ní nejsou žádné argumenty.</span><span class="sxs-lookup"><span data-stu-id="12d40-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="12d40-140">Je-li k dispozici více než jedna přetížená skupina, to znamená, že všechny požadované argumenty v jedné přetížené skupině jsou vázány a všechny argumenty v jiné přetížené skupině jsou také vázány.</span><span class="sxs-lookup"><span data-stu-id="12d40-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
