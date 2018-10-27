---
title: Povinné argumenty a skupiny přetížení
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: d7cfe00d93f1eede77bcda5881c63843722c9a17
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452898"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="b5629-102">Povinné argumenty a skupiny přetížení</span><span class="sxs-lookup"><span data-stu-id="b5629-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="b5629-103">Aktivity lze nastavit tak, aby některé argumenty jsou povinné vázat pro aktivitu platná pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="b5629-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="b5629-104">`RequiredArgument` Atribut se používá k označení, že se vyžadují některé argumenty pro aktivitu a `OverloadGroup` atribut se používá k seskupení kategorie povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="b5629-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="b5629-105">Pomocí atributů lze aktivity autoři uvádějí aktivitu jednoduchých nebo složitých ověření konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b5629-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="b5629-106">Povinné argumenty</span><span class="sxs-lookup"><span data-stu-id="b5629-106">Using Required Arguments</span></span>  
 <span data-ttu-id="b5629-107">Použít `RequiredArgument` atribut v aktivitě, označení požadovaného argumentů pomocí <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b5629-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="b5629-108">V tomto příkladu `Add` aktivity je definován, že má dvě povinné argumenty.</span><span class="sxs-lookup"><span data-stu-id="b5629-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="b5629-109">V XAML, povinnými argumenty jsou také uvedeny pomocí <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b5629-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="b5629-110">V tomto příkladu `Add` aktivity je definován pomocí tří argumentů a použije <xref:System.Activities.Statements.Assign%601> aktivita k provedení operace přidání.</span><span class="sxs-lookup"><span data-stu-id="b5629-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="b5629-111">Pokud se používá aktivitu a není vázaná buď povinnými argumenty vrátil následující chybu ověření.</span><span class="sxs-lookup"><span data-stu-id="b5629-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="b5629-112">**Nebyla zadána hodnota pro povinný argument aktivity "Operand1".**</span><span class="sxs-lookup"><span data-stu-id="b5629-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="b5629-113">Další informace o zjišťování a zpracování chyby a upozornění ověření najdete v tématu [vyvolání ověřování aktivit](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="b5629-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="b5629-114">Používání skupiny přetížení</span><span class="sxs-lookup"><span data-stu-id="b5629-114">Using Overload Groups</span></span>

<span data-ttu-id="b5629-115">Přetížené skupiny poskytují metoda označující, jaké kombinace argumentů jsou platné v nějaké aktivitě.</span><span class="sxs-lookup"><span data-stu-id="b5629-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="b5629-116">Argumenty jsou seskupené dohromady pomocí <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b5629-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="b5629-117">Každá skupina je přiřazen název, který je určen <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b5629-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="b5629-118">Aktivita je platný, pokud jsou svázány pouze jednu sadu argumentů v přetížené skupině.</span><span class="sxs-lookup"><span data-stu-id="b5629-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="b5629-119">V následujícím příkladu `CreateLocation` třída je definována.</span><span class="sxs-lookup"><span data-stu-id="b5629-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="b5629-120">Cílem této aktivity je a zadejte umístění v USA.</span><span class="sxs-lookup"><span data-stu-id="b5629-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="b5629-121">K tomuto účelu můžete zadat uživatelské aktivity umístění pomocí jedné ze tří skupin argumentů.</span><span class="sxs-lookup"><span data-stu-id="b5629-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="b5629-122">Chcete-li určit platné kombinace argumentů, jsou definovány tři přetížené skupiny.</span><span class="sxs-lookup"><span data-stu-id="b5629-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="b5629-123">`G1` obsahuje `Latitude` a `Longitude` argumenty.</span><span class="sxs-lookup"><span data-stu-id="b5629-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="b5629-124">`G2` obsahuje `Street`, `City`, a `State`.</span><span class="sxs-lookup"><span data-stu-id="b5629-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="b5629-125">`G3` obsahuje `Street` a `Zip`.</span><span class="sxs-lookup"><span data-stu-id="b5629-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="b5629-126">`Name` je také požadovaný argument, ale není součástí skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="b5629-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="b5629-127">Pro tuto aktivitu platná `Name` musel být vázaný spolu s všechny argumenty z jeden a pouze jednu přetíženou skupinu.</span><span class="sxs-lookup"><span data-stu-id="b5629-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="b5629-128">V následujícím příkladu se pořídí z [aktivity přístupu k databázi](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) ukázku, existují dvě přetížení skupin: `ConnectionString` a `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="b5629-128">In the following example, taken from the [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="b5629-129">Pro tuto aktivitu platit, buď `ProviderName` a `ConnectionString` argumenty musí být vázán, nebo `ConfigName` argument, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="b5629-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="b5629-130">Při definování přetížené skupiny:</span><span class="sxs-lookup"><span data-stu-id="b5629-130">When defining an overload group:</span></span>  
  
-   <span data-ttu-id="b5629-131">Přetížené skupiny nemůže být dílčí nebo ekvivalentní sadu jiného přetíženou skupinu.</span><span class="sxs-lookup"><span data-stu-id="b5629-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5629-132">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="b5629-132">There is one exception to this rule.</span></span> <span data-ttu-id="b5629-133">Pokud přetížené skupiny jsou podmnožinou jiné skupiny přetížení a dílčí obsahuje argumenty, pouze pokud `RequiredArgument` je `false`, přetíženou skupinu je platný.</span><span class="sxs-lookup"><span data-stu-id="b5629-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
-   <span data-ttu-id="b5629-134">Přetížené skupiny může dojít k překrytí, ale jedná se o chybu, pokud je určena průsečíkem skupiny obsahuje všechny požadované argumenty alespoň jednu z přetížených skupin.</span><span class="sxs-lookup"><span data-stu-id="b5629-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="b5629-135">V předchozím příkladu `G2` a `G3` přetížení překrývajících se skupiny, ale protože je určena průsečíkem neobsahovala všechny argumenty jednoho nebo obou skupin toto byla platná.</span><span class="sxs-lookup"><span data-stu-id="b5629-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="b5629-136">Při vytváření vazby argumenty v přetížené skupiny:</span><span class="sxs-lookup"><span data-stu-id="b5629-136">When binding arguments in an overload group:</span></span>  
  
-   <span data-ttu-id="b5629-137">Přetížené skupiny se považuje za mez, zda mají všechny `RequiredArgument` argumenty ve skupině jsou vázána.</span><span class="sxs-lookup"><span data-stu-id="b5629-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
-   <span data-ttu-id="b5629-138">Pokud má skupina nula `RequiredArgument` argumenty a aspoň jeden argument vázán, pak skupinu se považuje za s vazbou.</span><span class="sxs-lookup"><span data-stu-id="b5629-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
-   <span data-ttu-id="b5629-139">Je chyba ověřování, pokud žádné přetížené skupiny jsou vázány, není-li jednu přetíženou skupinu nemá žádné `RequiredArgument` argumenty v ní.</span><span class="sxs-lookup"><span data-stu-id="b5629-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
-   <span data-ttu-id="b5629-140">Jedná se o chybu mít více než jednu přetíženou skupinu vázán, který je, jsou vázána všechny požadované argumenty v jednu přetíženou skupinu a jsou svázaná některý argument v jiné skupině přetížení.</span><span class="sxs-lookup"><span data-stu-id="b5629-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
