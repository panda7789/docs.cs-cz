---
title: Vyžaduje argumenty a skupiny přetížení
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 794a0a531fbd26d9e4242d40be5147ab41547192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517557"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="4f50e-102">Vyžaduje argumenty a skupiny přetížení</span><span class="sxs-lookup"><span data-stu-id="4f50e-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="4f50e-103">Aktivity lze nakonfigurovat tak, aby některé argumenty jsou povinné vázat pro aktivitu platná pro provedení.</span><span class="sxs-lookup"><span data-stu-id="4f50e-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="4f50e-104">`RequiredArgument` Atribut slouží k označení, že některé argumenty u aktivit jsou povinné a `OverloadGroup` atribut slouží k seskupení kategorie povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="4f50e-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="4f50e-105">Pomocí atributy mohou aktivity tvůrci poskytnout jednoduché nebo komplexní aktivity ověření konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4f50e-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="4f50e-106">Pomocí povinnými argumenty</span><span class="sxs-lookup"><span data-stu-id="4f50e-106">Using Required Arguments</span></span>  
 <span data-ttu-id="4f50e-107">Použít `RequiredArgument` atribut v aktivitě, zda jsou požadované argumenty pomocí <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4f50e-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="4f50e-108">V tomto příkladu `Add` aktivity je definovaný, dvěma vyžaduje argumenty.</span><span class="sxs-lookup"><span data-stu-id="4f50e-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="4f50e-109">V jazyce XAML, povinnými argumenty jsou uvedeny i pomocí <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4f50e-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="4f50e-110">V tomto příkladu `Add` aktivity se definuje pomocí tří argumentů a používá <xref:System.Activities.Statements.Assign%601> aktivita k provedení operace přidání.</span><span class="sxs-lookup"><span data-stu-id="4f50e-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="4f50e-111">Pokud se používá aktivitu a není vázán buď povinnými argumenty se vrátí následující chybu ověřování.</span><span class="sxs-lookup"><span data-stu-id="4f50e-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="4f50e-112">**Nebyla zadána hodnota pro argument požadované aktivity 'Operand1'.**</span><span class="sxs-lookup"><span data-stu-id="4f50e-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
>  <span data-ttu-id="4f50e-113">Další informace o kontrole a zpracování chyb při ověřování a upozornění najdete v tématu [ověření aktivity vyvolání](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="4f50e-113">For more information about about checking for and handling validation errors and warnings, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="4f50e-114">Použití skupin přetížení</span><span class="sxs-lookup"><span data-stu-id="4f50e-114">Using Overload Groups</span></span>  
 <span data-ttu-id="4f50e-115">Přetížení skupiny zadejte metodu, která určuje, které kombinace argumenty jsou platné v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="4f50e-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="4f50e-116">Argumenty jsou seskupeny dohromady pomocí <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4f50e-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="4f50e-117">Každou skupinu je zadaný název, který je zadán <xref:System.Activities.OverloadGroupAttribute>, aktivita je platná, pokud je vázána jen jednu sadu argumentů ve skupině přetížení.</span><span class="sxs-lookup"><span data-stu-id="4f50e-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>, The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="4f50e-118">V následujícím příkladu převzaty z [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) ukázce `CreateLocation` třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="4f50e-118">In the following example, taken from the [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) sample, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="4f50e-119">Cílem této aktivity je zadejte umístění v USA.</span><span class="sxs-lookup"><span data-stu-id="4f50e-119">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="4f50e-120">K tomuto účelu uživatele aktivity umístění můžete zadat pomocí jednoho ze tří skupin argumentů.</span><span class="sxs-lookup"><span data-stu-id="4f50e-120">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="4f50e-121">Pokud chcete zadat platné kombinace argumenty, jsou definovány tři skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="4f50e-121">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="4f50e-122">`G1` obsahuje `Latitude` a `Longitude` argumenty.</span><span class="sxs-lookup"><span data-stu-id="4f50e-122">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="4f50e-123">`G2` obsahuje `Street`, `City`, a `State`.</span><span class="sxs-lookup"><span data-stu-id="4f50e-123">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="4f50e-124">`G3` obsahuje `Street` a `Zip`.</span><span class="sxs-lookup"><span data-stu-id="4f50e-124">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="4f50e-125">`Name` je také požadovaný argument, ale není součástí skupiny přetížení.</span><span class="sxs-lookup"><span data-stu-id="4f50e-125">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="4f50e-126">Pro tuto aktivitu platná `Name` by musel být vázána společně s všechny argumenty ze skupiny přetížení pouze jeden.</span><span class="sxs-lookup"><span data-stu-id="4f50e-126">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="4f50e-127">V následujícím příkladu převzaty z [databáze Access aktivity](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) ukázku, existují dvě přetížení skupin: `ConnectionString` a `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="4f50e-127">In the following example, taken from the [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="4f50e-128">Pro tuto aktivitu. Chcete-li být platný, buď `ProviderName` a `ConnectionString` argumenty musí být vázán, nebo `ConfigName` argument, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="4f50e-128">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="4f50e-129">Při definování skupinu přetížení:</span><span class="sxs-lookup"><span data-stu-id="4f50e-129">When defining an overload group:</span></span>  
  
-   <span data-ttu-id="4f50e-130">Skupinu přetížení nemůže být podmnožinu nebo ekvivalentní sadu jiné skupiny pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="4f50e-130">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f50e-131">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="4f50e-131">There is one exception to this rule.</span></span> <span data-ttu-id="4f50e-132">Pokud skupinu přetížení je podmnožinou jiné přetížení skupiny a do něj podmnožinu obsahuje pouze argumenty kde `RequiredArgument` je `false`, pak přetížení skupina je neplatná.</span><span class="sxs-lookup"><span data-stu-id="4f50e-132">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
-   <span data-ttu-id="4f50e-133">Přetížení skupiny může dojít k překrytí, ale jedná se o chybu, pokud průniku skupiny obsahuje všechny požadované argumenty jednoho nebo obou skupin přetížení.</span><span class="sxs-lookup"><span data-stu-id="4f50e-133">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="4f50e-134">V předchozím příkladu `G2` a `G3` přetížení skupiny překryté, ale protože průnik neobsahoval všechny argumenty jednoho nebo obou skupin byla platná.</span><span class="sxs-lookup"><span data-stu-id="4f50e-134">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="4f50e-135">Při vytváření vazby argumenty ve skupině přetížení:</span><span class="sxs-lookup"><span data-stu-id="4f50e-135">When binding arguments in an overload group:</span></span>  
  
-   <span data-ttu-id="4f50e-136">Skupinu přetížení je považována za hranice, pokud všechny `RequiredArgument` argumenty ve skupině je vázána.</span><span class="sxs-lookup"><span data-stu-id="4f50e-136">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
-   <span data-ttu-id="4f50e-137">Pokud skupina má nula `RequiredArgument` argumentů a alespoň jeden argument vázán, pak skupinu se považuje za hranice.</span><span class="sxs-lookup"><span data-stu-id="4f50e-137">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
-   <span data-ttu-id="4f50e-138">Pokud žádné přetížení skupiny jsou svázané s Pokud jedna skupina přetížení neobsahuje žádné je chyba ověření `RequiredArgument` argumenty v ní.</span><span class="sxs-lookup"><span data-stu-id="4f50e-138">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
-   <span data-ttu-id="4f50e-139">Jedná se o chybu do mají více než jednu skupinu přetížení vázán, který je, všechny požadované argumenty ve skupině jedním přetížením jsou svázané s a také vázán některý argument v jiné skupině přetížení.</span><span class="sxs-lookup"><span data-stu-id="4f50e-139">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
