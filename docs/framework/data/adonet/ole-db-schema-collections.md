---
title: Kolekce schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164681"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="6bcd3-102">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="6bcd3-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="6bcd3-103">Tato část popisuje kolekci podpora schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="6bcd3-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="6bcd3-104">Zprostředkovatel Microsoft SQL serveru OLE DB</span><span class="sxs-lookup"><span data-stu-id="6bcd3-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="6bcd3-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="6bcd3-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6bcd3-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="6bcd3-106">Tables</span></span>  
  
-   <span data-ttu-id="6bcd3-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-107">Columns</span></span>  
  
-   <span data-ttu-id="6bcd3-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="6bcd3-108">Procedures</span></span>  
  
-   <span data-ttu-id="6bcd3-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6bcd3-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="6bcd3-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="6bcd3-110">Catalog</span></span>  
  
-   <span data-ttu-id="6bcd3-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="6bcd3-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6bcd3-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="6bcd3-112">Tables</span></span>  
  
|<span data-ttu-id="6bcd3-113">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-113">ColumnName</span></span>|<span data-ttu-id="6bcd3-114">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-115">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-116">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-116">String</span></span>|  
|<span data-ttu-id="6bcd3-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-118">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-118">String</span></span>|  
|<span data-ttu-id="6bcd3-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-119">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-120">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-120">String</span></span>|  
|<span data-ttu-id="6bcd3-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-121">TABLE_TYPE</span></span>|<span data-ttu-id="6bcd3-122">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-122">String</span></span>|  
|<span data-ttu-id="6bcd3-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-123">TABLE_GUID</span></span>|<span data-ttu-id="6bcd3-124">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-124">Guid</span></span>|  
|<span data-ttu-id="6bcd3-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-125">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-126">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-126">String</span></span>|  
|<span data-ttu-id="6bcd3-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-127">TABLE_PROPID</span></span>|<span data-ttu-id="6bcd3-128">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-128">Int64</span></span>|  
|<span data-ttu-id="6bcd3-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-129">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-130">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-131">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6bcd3-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-133">Columns</span></span>  
  
|<span data-ttu-id="6bcd3-134">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-134">ColumnName</span></span>|<span data-ttu-id="6bcd3-135">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-136">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-137">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-137">String</span></span>|  
|<span data-ttu-id="6bcd3-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-139">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-139">String</span></span>|  
|<span data-ttu-id="6bcd3-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-140">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-141">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-141">String</span></span>|  
|<span data-ttu-id="6bcd3-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-142">COLUMN_NAME</span></span>|<span data-ttu-id="6bcd3-143">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-143">String</span></span>|  
|<span data-ttu-id="6bcd3-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-144">COLUMN_GUID</span></span>|<span data-ttu-id="6bcd3-145">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-145">Guid</span></span>|  
|<span data-ttu-id="6bcd3-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-146">COLUMN_PROPID</span></span>|<span data-ttu-id="6bcd3-147">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-147">Int64</span></span>|  
|<span data-ttu-id="6bcd3-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-149">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-149">Int64</span></span>|  
|<span data-ttu-id="6bcd3-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6bcd3-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-151">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6bcd3-153">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-153">String</span></span>|  
|<span data-ttu-id="6bcd3-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="6bcd3-155">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-155">Int64</span></span>|  
|<span data-ttu-id="6bcd3-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-156">IS_NULLABLE</span></span>|<span data-ttu-id="6bcd3-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-157">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-158">DATA_TYPE</span></span>|<span data-ttu-id="6bcd3-159">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-159">Int32</span></span>|  
|<span data-ttu-id="6bcd3-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-160">TYPE_GUID</span></span>|<span data-ttu-id="6bcd3-161">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-161">Guid</span></span>|  
|<span data-ttu-id="6bcd3-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6bcd3-163">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-163">Int64</span></span>|  
|<span data-ttu-id="6bcd3-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6bcd3-165">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-165">Int64</span></span>|  
|<span data-ttu-id="6bcd3-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6bcd3-167">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-167">Int32</span></span>|  
|<span data-ttu-id="6bcd3-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="6bcd3-169">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-169">Int16</span></span>|  
|<span data-ttu-id="6bcd3-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="6bcd3-171">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-171">Int64</span></span>|  
|<span data-ttu-id="6bcd3-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6bcd3-173">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-173">String</span></span>|  
|<span data-ttu-id="6bcd3-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6bcd3-175">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-175">String</span></span>|  
|<span data-ttu-id="6bcd3-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6bcd3-177">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-177">String</span></span>|  
|<span data-ttu-id="6bcd3-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="6bcd3-179">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-179">String</span></span>|  
|<span data-ttu-id="6bcd3-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6bcd3-181">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-181">String</span></span>|  
|<span data-ttu-id="6bcd3-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-182">COLLATION_NAME</span></span>|<span data-ttu-id="6bcd3-183">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-183">String</span></span>|  
|<span data-ttu-id="6bcd3-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6bcd3-185">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-185">String</span></span>|  
|<span data-ttu-id="6bcd3-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6bcd3-187">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-187">String</span></span>|  
|<span data-ttu-id="6bcd3-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-188">DOMAIN_NAME</span></span>|<span data-ttu-id="6bcd3-189">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-189">String</span></span>|  
|<span data-ttu-id="6bcd3-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-190">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-191">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-191">String</span></span>|  
|<span data-ttu-id="6bcd3-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-192">COLUMN_LCID</span></span>|<span data-ttu-id="6bcd3-193">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-193">Int32</span></span>|  
|<span data-ttu-id="6bcd3-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="6bcd3-195">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-195">Int32</span></span>|  
|<span data-ttu-id="6bcd3-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-196">COLUMN_SORTID</span></span>|<span data-ttu-id="6bcd3-197">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-197">Int32</span></span>|  
|<span data-ttu-id="6bcd3-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="6bcd3-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="6bcd3-199">Byte[]</span></span>|  
|<span data-ttu-id="6bcd3-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-200">IS_COMPUTED</span></span>|<span data-ttu-id="6bcd3-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6bcd3-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="6bcd3-202">Procedures</span></span>  
  
|<span data-ttu-id="6bcd3-203">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-203">ColumnName</span></span>|<span data-ttu-id="6bcd3-204">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6bcd3-206">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-206">String</span></span>|  
|<span data-ttu-id="6bcd3-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-208">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-208">String</span></span>|  
|<span data-ttu-id="6bcd3-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="6bcd3-210">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-210">String</span></span>|  
|<span data-ttu-id="6bcd3-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6bcd3-212">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-212">Int16</span></span>|  
|<span data-ttu-id="6bcd3-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6bcd3-214">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-214">String</span></span>|  
|<span data-ttu-id="6bcd3-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-215">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-216">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-216">String</span></span>|  
|<span data-ttu-id="6bcd3-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-217">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-218">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-219">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="6bcd3-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6bcd3-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="6bcd3-222">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-222">ColumnName</span></span>|<span data-ttu-id="6bcd3-223">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6bcd3-225">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-225">String</span></span>|  
|<span data-ttu-id="6bcd3-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-227">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-227">String</span></span>|  
|<span data-ttu-id="6bcd3-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="6bcd3-229">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-229">String</span></span>|  
|<span data-ttu-id="6bcd3-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-230">PARAMETER_NAME</span></span>|<span data-ttu-id="6bcd3-231">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-231">String</span></span>|  
|<span data-ttu-id="6bcd3-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-233">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-233">Int32</span></span>|  
|<span data-ttu-id="6bcd3-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="6bcd3-235">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-235">Int32</span></span>|  
|<span data-ttu-id="6bcd3-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="6bcd3-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-237">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="6bcd3-239">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-239">String</span></span>|  
|<span data-ttu-id="6bcd3-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-240">IS_NULLABLE</span></span>|<span data-ttu-id="6bcd3-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-241">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-242">DATA_TYPE</span></span>|<span data-ttu-id="6bcd3-243">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-243">Int32</span></span>|  
|<span data-ttu-id="6bcd3-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6bcd3-245">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-245">Int64</span></span>|  
|<span data-ttu-id="6bcd3-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6bcd3-247">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-247">Int64</span></span>|  
|<span data-ttu-id="6bcd3-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6bcd3-249">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-249">Int32</span></span>|  
|<span data-ttu-id="6bcd3-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="6bcd3-251">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-251">Int16</span></span>|  
|<span data-ttu-id="6bcd3-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-252">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-253">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-253">String</span></span>|  
|<span data-ttu-id="6bcd3-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-254">TYPE_NAME</span></span>|<span data-ttu-id="6bcd3-255">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-255">String</span></span>|  
|<span data-ttu-id="6bcd3-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="6bcd3-257">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="6bcd3-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="6bcd3-258">Catalog</span></span>  
  
|<span data-ttu-id="6bcd3-259">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-259">ColumnName</span></span>|<span data-ttu-id="6bcd3-260">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-261">CATALOG_NAME</span></span>|<span data-ttu-id="6bcd3-262">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-262">String</span></span>|  
|<span data-ttu-id="6bcd3-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-263">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-264">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6bcd3-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="6bcd3-265">Indexes</span></span>  
  
|<span data-ttu-id="6bcd3-266">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-266">ColumnName</span></span>|<span data-ttu-id="6bcd3-267">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-268">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-269">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-269">String</span></span>|  
|<span data-ttu-id="6bcd3-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-271">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-271">String</span></span>|  
|<span data-ttu-id="6bcd3-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-272">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-273">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-273">String</span></span>|  
|<span data-ttu-id="6bcd3-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-274">INDEX_CATALOG</span></span>|<span data-ttu-id="6bcd3-275">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-275">String</span></span>|  
|<span data-ttu-id="6bcd3-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="6bcd3-277">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-277">String</span></span>|  
|<span data-ttu-id="6bcd3-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-278">INDEX_NAME</span></span>|<span data-ttu-id="6bcd3-279">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-279">String</span></span>|  
|<span data-ttu-id="6bcd3-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6bcd3-280">PRIMARY_KEY</span></span>|<span data-ttu-id="6bcd3-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-281">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-282">UNIQUE</span></span>|<span data-ttu-id="6bcd3-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-283">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-284">CLUSTERED</span></span>|<span data-ttu-id="6bcd3-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-285">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-286">TYP</span><span class="sxs-lookup"><span data-stu-id="6bcd3-286">TYPE</span></span>|<span data-ttu-id="6bcd3-287">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-287">Int32</span></span>|  
|<span data-ttu-id="6bcd3-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6bcd3-288">FILL_FACTOR</span></span>|<span data-ttu-id="6bcd3-289">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-289">Int32</span></span>|  
|<span data-ttu-id="6bcd3-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-290">INITIAL_SIZE</span></span>|<span data-ttu-id="6bcd3-291">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-291">Int32</span></span>|  
|<span data-ttu-id="6bcd3-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-292">NULLS</span></span>|<span data-ttu-id="6bcd3-293">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-293">Int32</span></span>|  
|<span data-ttu-id="6bcd3-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6bcd3-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-295">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-296">AUTO_UPDATE</span></span>|<span data-ttu-id="6bcd3-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-297">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-298">NULL_COLLATION</span></span>|<span data-ttu-id="6bcd3-299">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-299">Int32</span></span>|  
|<span data-ttu-id="6bcd3-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-301">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-301">Int64</span></span>|  
|<span data-ttu-id="6bcd3-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-302">COLUMN_NAME</span></span>|<span data-ttu-id="6bcd3-303">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-303">String</span></span>|  
|<span data-ttu-id="6bcd3-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-304">COLUMN_GUID</span></span>|<span data-ttu-id="6bcd3-305">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-305">Guid</span></span>|  
|<span data-ttu-id="6bcd3-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-306">COLUMN_PROPID</span></span>|<span data-ttu-id="6bcd3-307">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-307">Int64</span></span>|  
|<span data-ttu-id="6bcd3-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-308">COLLATION</span></span>|<span data-ttu-id="6bcd3-309">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-309">Int16</span></span>|  
|<span data-ttu-id="6bcd3-310">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-310">CARDINALITY</span></span>|<span data-ttu-id="6bcd3-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="6bcd3-311">Decimal</span></span>|  
|<span data-ttu-id="6bcd3-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="6bcd3-312">PAGES</span></span>|<span data-ttu-id="6bcd3-313">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-313">Int32</span></span>|  
|<span data-ttu-id="6bcd3-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-314">FILTER_CONDITION</span></span>|<span data-ttu-id="6bcd3-315">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-315">String</span></span>|  
|<span data-ttu-id="6bcd3-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="6bcd3-316">INTEGRATED</span></span>|<span data-ttu-id="6bcd3-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="6bcd3-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="6bcd3-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="6bcd3-319">Oracle OLE DB ovladač Microsoft podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="6bcd3-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6bcd3-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="6bcd3-320">Tables</span></span>  
  
-   <span data-ttu-id="6bcd3-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-321">Columns</span></span>  
  
-   <span data-ttu-id="6bcd3-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="6bcd3-322">Procedures</span></span>  
  
-   <span data-ttu-id="6bcd3-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6bcd3-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="6bcd3-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="6bcd3-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="6bcd3-325">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="6bcd3-325">Views</span></span>  
  
-   <span data-ttu-id="6bcd3-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="6bcd3-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6bcd3-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="6bcd3-327">Tables</span></span>  
  
|<span data-ttu-id="6bcd3-328">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-328">ColumnName</span></span>|<span data-ttu-id="6bcd3-329">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-330">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-331">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-331">String</span></span>|  
|<span data-ttu-id="6bcd3-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-333">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-333">String</span></span>|  
|<span data-ttu-id="6bcd3-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-334">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-335">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-335">String</span></span>|  
|<span data-ttu-id="6bcd3-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-336">TABLE_TYPE</span></span>|<span data-ttu-id="6bcd3-337">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-337">String</span></span>|  
|<span data-ttu-id="6bcd3-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-338">TABLE_GUID</span></span>|<span data-ttu-id="6bcd3-339">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-339">Guid</span></span>|  
|<span data-ttu-id="6bcd3-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-340">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-341">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-341">String</span></span>|  
|<span data-ttu-id="6bcd3-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-342">TABLE_PROPID</span></span>|<span data-ttu-id="6bcd3-343">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-343">Int64</span></span>|  
|<span data-ttu-id="6bcd3-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-344">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-345">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-346">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6bcd3-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-348">Columns</span></span>  
  
|<span data-ttu-id="6bcd3-349">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-349">ColumnName</span></span>|<span data-ttu-id="6bcd3-350">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-351">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-352">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-352">String</span></span>|  
|<span data-ttu-id="6bcd3-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-354">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-354">String</span></span>|  
|<span data-ttu-id="6bcd3-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-355">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-356">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-356">String</span></span>|  
|<span data-ttu-id="6bcd3-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-357">COLUMN_NAME</span></span>|<span data-ttu-id="6bcd3-358">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-358">String</span></span>|  
|<span data-ttu-id="6bcd3-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-359">COLUMN_GUID</span></span>|<span data-ttu-id="6bcd3-360">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-360">Guid</span></span>|  
|<span data-ttu-id="6bcd3-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-361">COLUMN_PROPID</span></span>|<span data-ttu-id="6bcd3-362">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-362">Int64</span></span>|  
|<span data-ttu-id="6bcd3-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-364">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-364">Int64</span></span>|  
|<span data-ttu-id="6bcd3-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6bcd3-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-366">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6bcd3-368">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-368">String</span></span>|  
|<span data-ttu-id="6bcd3-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="6bcd3-370">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-370">Int64</span></span>|  
|<span data-ttu-id="6bcd3-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-371">IS_NULLABLE</span></span>|<span data-ttu-id="6bcd3-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-372">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-373">DATA_TYPE</span></span>|<span data-ttu-id="6bcd3-374">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-374">Int32</span></span>|  
|<span data-ttu-id="6bcd3-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-375">TYPE_GUID</span></span>|<span data-ttu-id="6bcd3-376">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-376">Guid</span></span>|  
|<span data-ttu-id="6bcd3-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6bcd3-378">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-378">Int64</span></span>|  
|<span data-ttu-id="6bcd3-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6bcd3-380">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-380">Int64</span></span>|  
|<span data-ttu-id="6bcd3-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6bcd3-382">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-382">Int32</span></span>|  
|<span data-ttu-id="6bcd3-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="6bcd3-384">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-384">Int16</span></span>|  
|<span data-ttu-id="6bcd3-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="6bcd3-386">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-386">Int64</span></span>|  
|<span data-ttu-id="6bcd3-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6bcd3-388">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-388">String</span></span>|  
|<span data-ttu-id="6bcd3-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6bcd3-390">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-390">String</span></span>|  
|<span data-ttu-id="6bcd3-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6bcd3-392">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-392">String</span></span>|  
|<span data-ttu-id="6bcd3-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="6bcd3-394">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-394">String</span></span>|  
|<span data-ttu-id="6bcd3-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6bcd3-396">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-396">String</span></span>|  
|<span data-ttu-id="6bcd3-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-397">COLLATION_NAME</span></span>|<span data-ttu-id="6bcd3-398">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-398">String</span></span>|  
|<span data-ttu-id="6bcd3-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6bcd3-400">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-400">String</span></span>|  
|<span data-ttu-id="6bcd3-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6bcd3-402">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-402">String</span></span>|  
|<span data-ttu-id="6bcd3-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-403">DOMAIN_NAME</span></span>|<span data-ttu-id="6bcd3-404">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-404">String</span></span>|  
|<span data-ttu-id="6bcd3-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-405">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-406">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6bcd3-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="6bcd3-407">Procedures</span></span>  
  
|<span data-ttu-id="6bcd3-408">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-408">ColumnName</span></span>|<span data-ttu-id="6bcd3-409">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6bcd3-411">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-411">String</span></span>|  
|<span data-ttu-id="6bcd3-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-413">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-413">String</span></span>|  
|<span data-ttu-id="6bcd3-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="6bcd3-415">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-415">String</span></span>|  
|<span data-ttu-id="6bcd3-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6bcd3-417">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-417">Int16</span></span>|  
|<span data-ttu-id="6bcd3-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6bcd3-419">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-419">String</span></span>|  
|<span data-ttu-id="6bcd3-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-420">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-421">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-421">String</span></span>|  
|<span data-ttu-id="6bcd3-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-422">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-423">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-424">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="6bcd3-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="6bcd3-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="6bcd3-427">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-427">ColumnName</span></span>|<span data-ttu-id="6bcd3-428">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6bcd3-430">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-430">String</span></span>|  
|<span data-ttu-id="6bcd3-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-432">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-432">String</span></span>|  
|<span data-ttu-id="6bcd3-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="6bcd3-434">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-434">String</span></span>|  
|<span data-ttu-id="6bcd3-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-435">COLUMN_NAME</span></span>|<span data-ttu-id="6bcd3-436">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-436">String</span></span>|  
|<span data-ttu-id="6bcd3-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-437">COLUMN_GUID</span></span>|<span data-ttu-id="6bcd3-438">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-438">Guid</span></span>|  
|<span data-ttu-id="6bcd3-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-439">COLUMN_PROPID</span></span>|<span data-ttu-id="6bcd3-440">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-440">Int64</span></span>|  
|<span data-ttu-id="6bcd3-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="6bcd3-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="6bcd3-442">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-442">Int64</span></span>|  
|<span data-ttu-id="6bcd3-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-444">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-444">Int64</span></span>|  
|<span data-ttu-id="6bcd3-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-445">IS_NULLABLE</span></span>|<span data-ttu-id="6bcd3-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-446">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-447">DATA_TYPE</span></span>|<span data-ttu-id="6bcd3-448">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-448">Int32</span></span>|  
|<span data-ttu-id="6bcd3-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-449">TYPE_GUID</span></span>|<span data-ttu-id="6bcd3-450">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-450">Guid</span></span>|  
|<span data-ttu-id="6bcd3-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6bcd3-452">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-452">Int64</span></span>|  
|<span data-ttu-id="6bcd3-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6bcd3-454">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-454">Int64</span></span>|  
|<span data-ttu-id="6bcd3-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6bcd3-456">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-456">Int32</span></span>|  
|<span data-ttu-id="6bcd3-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="6bcd3-458">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-458">Int16</span></span>|  
|<span data-ttu-id="6bcd3-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-459">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-460">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-460">String</span></span>|  
|<span data-ttu-id="6bcd3-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="6bcd3-461">OVERLOAD</span></span>|<span data-ttu-id="6bcd3-462">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6bcd3-463">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="6bcd3-463">Views</span></span>  
  
|<span data-ttu-id="6bcd3-464">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-464">ColumnName</span></span>|<span data-ttu-id="6bcd3-465">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-466">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-467">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-467">String</span></span>|  
|<span data-ttu-id="6bcd3-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-469">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-469">String</span></span>|  
|<span data-ttu-id="6bcd3-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-470">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-471">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-471">String</span></span>|  
|<span data-ttu-id="6bcd3-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="6bcd3-473">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-473">String</span></span>|  
|<span data-ttu-id="6bcd3-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-474">CHECK_OPTION</span></span>|<span data-ttu-id="6bcd3-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-475">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-476">IS_UPDATABLE</span></span>|<span data-ttu-id="6bcd3-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-477">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-478">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-479">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-479">String</span></span>|  
|<span data-ttu-id="6bcd3-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-480">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-481">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-482">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6bcd3-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="6bcd3-484">Indexes</span></span>  
  
|<span data-ttu-id="6bcd3-485">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-485">ColumnName</span></span>|<span data-ttu-id="6bcd3-486">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-487">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-488">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-488">String</span></span>|  
|<span data-ttu-id="6bcd3-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-490">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-490">String</span></span>|  
|<span data-ttu-id="6bcd3-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-491">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-492">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-492">String</span></span>|  
|<span data-ttu-id="6bcd3-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-493">INDEX_CATALOG</span></span>|<span data-ttu-id="6bcd3-494">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-494">String</span></span>|  
|<span data-ttu-id="6bcd3-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="6bcd3-496">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-496">String</span></span>|  
|<span data-ttu-id="6bcd3-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-497">INDEX_NAME</span></span>|<span data-ttu-id="6bcd3-498">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-498">String</span></span>|  
|<span data-ttu-id="6bcd3-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6bcd3-499">PRIMARY_KEY</span></span>|<span data-ttu-id="6bcd3-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-500">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-501">UNIQUE</span></span>|<span data-ttu-id="6bcd3-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-502">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-503">CLUSTERED</span></span>|<span data-ttu-id="6bcd3-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-504">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-505">TYP</span><span class="sxs-lookup"><span data-stu-id="6bcd3-505">TYPE</span></span>|<span data-ttu-id="6bcd3-506">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-506">Int32</span></span>|  
|<span data-ttu-id="6bcd3-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6bcd3-507">FILL_FACTOR</span></span>|<span data-ttu-id="6bcd3-508">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-508">Int32</span></span>|  
|<span data-ttu-id="6bcd3-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-509">INITIAL_SIZE</span></span>|<span data-ttu-id="6bcd3-510">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-510">Int32</span></span>|  
|<span data-ttu-id="6bcd3-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-511">NULLS</span></span>|<span data-ttu-id="6bcd3-512">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-512">Int32</span></span>|  
|<span data-ttu-id="6bcd3-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6bcd3-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-514">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-515">AUTO_UPDATE</span></span>|<span data-ttu-id="6bcd3-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-516">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-517">NULL_COLLATION</span></span>|<span data-ttu-id="6bcd3-518">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-518">Int32</span></span>|  
|<span data-ttu-id="6bcd3-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-520">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-520">Int64</span></span>|  
|<span data-ttu-id="6bcd3-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-521">COLUMN_NAME</span></span>|<span data-ttu-id="6bcd3-522">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-522">String</span></span>|  
|<span data-ttu-id="6bcd3-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-523">COLUMN_GUID</span></span>|<span data-ttu-id="6bcd3-524">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-524">Guid</span></span>|  
|<span data-ttu-id="6bcd3-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-525">COLUMN_PROPID</span></span>|<span data-ttu-id="6bcd3-526">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-526">Int64</span></span>|  
|<span data-ttu-id="6bcd3-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-527">COLLATION</span></span>|<span data-ttu-id="6bcd3-528">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-528">Int16</span></span>|  
|<span data-ttu-id="6bcd3-529">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-529">CARDINALITY</span></span>|<span data-ttu-id="6bcd3-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="6bcd3-530">Decimal</span></span>|  
|<span data-ttu-id="6bcd3-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="6bcd3-531">PAGES</span></span>|<span data-ttu-id="6bcd3-532">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-532">Int32</span></span>|  
|<span data-ttu-id="6bcd3-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-533">FILTER_CONDITION</span></span>|<span data-ttu-id="6bcd3-534">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-534">String</span></span>|  
|<span data-ttu-id="6bcd3-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="6bcd3-535">INTEGRATED</span></span>|<span data-ttu-id="6bcd3-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="6bcd3-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="6bcd3-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="6bcd3-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="6bcd3-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="6bcd3-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="6bcd3-539">Tables</span></span>  
  
-   <span data-ttu-id="6bcd3-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-540">Columns</span></span>  
  
-   <span data-ttu-id="6bcd3-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="6bcd3-541">Procedures</span></span>  
  
-   <span data-ttu-id="6bcd3-542">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="6bcd3-542">Views</span></span>  
  
-   <span data-ttu-id="6bcd3-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="6bcd3-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="6bcd3-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="6bcd3-544">Tables</span></span>  
  
|<span data-ttu-id="6bcd3-545">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-545">ColumnName</span></span>|<span data-ttu-id="6bcd3-546">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-547">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-548">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-548">String</span></span>|  
|<span data-ttu-id="6bcd3-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-550">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-550">String</span></span>|  
|<span data-ttu-id="6bcd3-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-551">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-552">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-552">String</span></span>|  
|<span data-ttu-id="6bcd3-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-553">TABLE_TYPE</span></span>|<span data-ttu-id="6bcd3-554">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-554">String</span></span>|  
|<span data-ttu-id="6bcd3-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-555">TABLE_GUID</span></span>|<span data-ttu-id="6bcd3-556">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-556">Guid</span></span>|  
|<span data-ttu-id="6bcd3-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-557">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-558">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-558">String</span></span>|  
|<span data-ttu-id="6bcd3-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-559">TABLE_PROPID</span></span>|<span data-ttu-id="6bcd3-560">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-560">Int64</span></span>|  
|<span data-ttu-id="6bcd3-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-561">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-562">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-563">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="6bcd3-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-565">Columns</span></span>  
  
|<span data-ttu-id="6bcd3-566">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-566">ColumnName</span></span>|<span data-ttu-id="6bcd3-567">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-568">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-569">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-569">String</span></span>|  
|<span data-ttu-id="6bcd3-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-571">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-571">String</span></span>|  
|<span data-ttu-id="6bcd3-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-572">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-573">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-573">String</span></span>|  
|<span data-ttu-id="6bcd3-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-574">COLUMN_NAME</span></span>|<span data-ttu-id="6bcd3-575">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-575">String</span></span>|  
|<span data-ttu-id="6bcd3-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-576">COLUMN_GUID</span></span>|<span data-ttu-id="6bcd3-577">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-577">Guid</span></span>|  
|<span data-ttu-id="6bcd3-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-578">COLUMN_PROPID</span></span>|<span data-ttu-id="6bcd3-579">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-579">Int64</span></span>|  
|<span data-ttu-id="6bcd3-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-581">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-581">Int64</span></span>|  
|<span data-ttu-id="6bcd3-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="6bcd3-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-583">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="6bcd3-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="6bcd3-585">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-585">String</span></span>|  
|<span data-ttu-id="6bcd3-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="6bcd3-587">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-587">Int64</span></span>|  
|<span data-ttu-id="6bcd3-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-588">IS_NULLABLE</span></span>|<span data-ttu-id="6bcd3-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-589">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-590">DATA_TYPE</span></span>|<span data-ttu-id="6bcd3-591">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-591">Int32</span></span>|  
|<span data-ttu-id="6bcd3-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-592">TYPE_GUID</span></span>|<span data-ttu-id="6bcd3-593">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-593">Guid</span></span>|  
|<span data-ttu-id="6bcd3-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="6bcd3-595">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-595">Int64</span></span>|  
|<span data-ttu-id="6bcd3-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6bcd3-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="6bcd3-597">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-597">Int64</span></span>|  
|<span data-ttu-id="6bcd3-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="6bcd3-599">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-599">Int32</span></span>|  
|<span data-ttu-id="6bcd3-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="6bcd3-601">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-601">Int16</span></span>|  
|<span data-ttu-id="6bcd3-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="6bcd3-603">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-603">Int64</span></span>|  
|<span data-ttu-id="6bcd3-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="6bcd3-605">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-605">String</span></span>|  
|<span data-ttu-id="6bcd3-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="6bcd3-607">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-607">String</span></span>|  
|<span data-ttu-id="6bcd3-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="6bcd3-609">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-609">String</span></span>|  
|<span data-ttu-id="6bcd3-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="6bcd3-611">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-611">String</span></span>|  
|<span data-ttu-id="6bcd3-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="6bcd3-613">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-613">String</span></span>|  
|<span data-ttu-id="6bcd3-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-614">COLLATION_NAME</span></span>|<span data-ttu-id="6bcd3-615">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-615">String</span></span>|  
|<span data-ttu-id="6bcd3-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="6bcd3-617">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-617">String</span></span>|  
|<span data-ttu-id="6bcd3-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="6bcd3-619">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-619">String</span></span>|  
|<span data-ttu-id="6bcd3-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-620">DOMAIN_NAME</span></span>|<span data-ttu-id="6bcd3-621">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-621">String</span></span>|  
|<span data-ttu-id="6bcd3-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-622">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-623">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="6bcd3-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="6bcd3-624">Procedures</span></span>  
  
|<span data-ttu-id="6bcd3-625">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-625">ColumnName</span></span>|<span data-ttu-id="6bcd3-626">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="6bcd3-628">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-628">String</span></span>|  
|<span data-ttu-id="6bcd3-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-630">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-630">String</span></span>|  
|<span data-ttu-id="6bcd3-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="6bcd3-632">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-632">String</span></span>|  
|<span data-ttu-id="6bcd3-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="6bcd3-634">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-634">Int16</span></span>|  
|<span data-ttu-id="6bcd3-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="6bcd3-636">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-636">String</span></span>|  
|<span data-ttu-id="6bcd3-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-637">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-638">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-638">String</span></span>|  
|<span data-ttu-id="6bcd3-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-639">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-640">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-641">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="6bcd3-643">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="6bcd3-643">Views</span></span>  
  
|<span data-ttu-id="6bcd3-644">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-644">ColumnName</span></span>|<span data-ttu-id="6bcd3-645">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-646">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-647">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-647">String</span></span>|  
|<span data-ttu-id="6bcd3-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-649">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-649">String</span></span>|  
|<span data-ttu-id="6bcd3-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-650">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-651">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-651">String</span></span>|  
|<span data-ttu-id="6bcd3-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="6bcd3-653">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-653">String</span></span>|  
|<span data-ttu-id="6bcd3-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-654">CHECK_OPTION</span></span>|<span data-ttu-id="6bcd3-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-655">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-656">IS_UPDATABLE</span></span>|<span data-ttu-id="6bcd3-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-657">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-658">DESCRIPTION</span></span>|<span data-ttu-id="6bcd3-659">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-659">String</span></span>|  
|<span data-ttu-id="6bcd3-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-660">DATE_CREATED</span></span>|<span data-ttu-id="6bcd3-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-661">DateTime</span></span>|  
|<span data-ttu-id="6bcd3-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-662">DATE_MODIFIED</span></span>|<span data-ttu-id="6bcd3-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="6bcd3-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="6bcd3-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="6bcd3-664">Indexes</span></span>  
  
|<span data-ttu-id="6bcd3-665">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="6bcd3-665">ColumnName</span></span>|<span data-ttu-id="6bcd3-666">DataType</span><span class="sxs-lookup"><span data-stu-id="6bcd3-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="6bcd3-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-667">TABLE_CATALOG</span></span>|<span data-ttu-id="6bcd3-668">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-668">String</span></span>|  
|<span data-ttu-id="6bcd3-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="6bcd3-670">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-670">String</span></span>|  
|<span data-ttu-id="6bcd3-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-671">TABLE_NAME</span></span>|<span data-ttu-id="6bcd3-672">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-672">String</span></span>|  
|<span data-ttu-id="6bcd3-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="6bcd3-673">INDEX_CATALOG</span></span>|<span data-ttu-id="6bcd3-674">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-674">String</span></span>|  
|<span data-ttu-id="6bcd3-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="6bcd3-676">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-676">String</span></span>|  
|<span data-ttu-id="6bcd3-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-677">INDEX_NAME</span></span>|<span data-ttu-id="6bcd3-678">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-678">String</span></span>|  
|<span data-ttu-id="6bcd3-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="6bcd3-679">PRIMARY_KEY</span></span>|<span data-ttu-id="6bcd3-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-680">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-681">UNIQUE</span></span>|<span data-ttu-id="6bcd3-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-682">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="6bcd3-683">CLUSTERED</span></span>|<span data-ttu-id="6bcd3-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-684">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-685">TYP</span><span class="sxs-lookup"><span data-stu-id="6bcd3-685">TYPE</span></span>|<span data-ttu-id="6bcd3-686">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-686">Int32</span></span>|  
|<span data-ttu-id="6bcd3-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="6bcd3-687">FILL_FACTOR</span></span>|<span data-ttu-id="6bcd3-688">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-688">Int32</span></span>|  
|<span data-ttu-id="6bcd3-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-689">INITIAL_SIZE</span></span>|<span data-ttu-id="6bcd3-690">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-690">Int32</span></span>|  
|<span data-ttu-id="6bcd3-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-691">NULLS</span></span>|<span data-ttu-id="6bcd3-692">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-692">Int32</span></span>|  
|<span data-ttu-id="6bcd3-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="6bcd3-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="6bcd3-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-694">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-695">AUTO_UPDATE</span></span>|<span data-ttu-id="6bcd3-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-696">Boolean</span></span>|  
|<span data-ttu-id="6bcd3-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-697">NULL_COLLATION</span></span>|<span data-ttu-id="6bcd3-698">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-698">Int32</span></span>|  
|<span data-ttu-id="6bcd3-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="6bcd3-700">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-700">Int64</span></span>|  
|<span data-ttu-id="6bcd3-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6bcd3-701">COLUMN_NAME</span></span>|<span data-ttu-id="6bcd3-702">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-702">String</span></span>|  
|<span data-ttu-id="6bcd3-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-703">COLUMN_GUID</span></span>|<span data-ttu-id="6bcd3-704">Guid</span><span class="sxs-lookup"><span data-stu-id="6bcd3-704">Guid</span></span>|  
|<span data-ttu-id="6bcd3-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="6bcd3-705">COLUMN_PROPID</span></span>|<span data-ttu-id="6bcd3-706">Int64</span><span class="sxs-lookup"><span data-stu-id="6bcd3-706">Int64</span></span>|  
|<span data-ttu-id="6bcd3-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="6bcd3-707">COLLATION</span></span>|<span data-ttu-id="6bcd3-708">Int16</span><span class="sxs-lookup"><span data-stu-id="6bcd3-708">Int16</span></span>|  
|<span data-ttu-id="6bcd3-709">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="6bcd3-709">CARDINALITY</span></span>|<span data-ttu-id="6bcd3-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="6bcd3-710">Decimal</span></span>|  
|<span data-ttu-id="6bcd3-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="6bcd3-711">PAGES</span></span>|<span data-ttu-id="6bcd3-712">Int32</span><span class="sxs-lookup"><span data-stu-id="6bcd3-712">Int32</span></span>|  
|<span data-ttu-id="6bcd3-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="6bcd3-713">FILTER_CONDITION</span></span>|<span data-ttu-id="6bcd3-714">String</span><span class="sxs-lookup"><span data-stu-id="6bcd3-714">String</span></span>|  
|<span data-ttu-id="6bcd3-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="6bcd3-715">INTEGRATED</span></span>|<span data-ttu-id="6bcd3-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="6bcd3-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bcd3-717">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bcd3-717">See also</span></span>

- [<span data-ttu-id="6bcd3-718">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="6bcd3-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
