---
title: Kolekce schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771992"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="24edb-102">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="24edb-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="24edb-103">Tato část popisuje kolekci podpora schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="24edb-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="24edb-104">Zprostředkovatel Microsoft SQL serveru OLE DB</span><span class="sxs-lookup"><span data-stu-id="24edb-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="24edb-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="24edb-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="24edb-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="24edb-106">Tables</span></span>  
  
- <span data-ttu-id="24edb-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-107">Columns</span></span>  
  
- <span data-ttu-id="24edb-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="24edb-108">Procedures</span></span>  
  
- <span data-ttu-id="24edb-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="24edb-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="24edb-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="24edb-110">Catalog</span></span>  
  
- <span data-ttu-id="24edb-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="24edb-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="24edb-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="24edb-112">Tables</span></span>  
  
|<span data-ttu-id="24edb-113">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-113">ColumnName</span></span>|<span data-ttu-id="24edb-114">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-115">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-116">String</span><span class="sxs-lookup"><span data-stu-id="24edb-116">String</span></span>|  
|<span data-ttu-id="24edb-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-118">String</span><span class="sxs-lookup"><span data-stu-id="24edb-118">String</span></span>|  
|<span data-ttu-id="24edb-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-119">TABLE_NAME</span></span>|<span data-ttu-id="24edb-120">String</span><span class="sxs-lookup"><span data-stu-id="24edb-120">String</span></span>|  
|<span data-ttu-id="24edb-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-121">TABLE_TYPE</span></span>|<span data-ttu-id="24edb-122">String</span><span class="sxs-lookup"><span data-stu-id="24edb-122">String</span></span>|  
|<span data-ttu-id="24edb-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-123">TABLE_GUID</span></span>|<span data-ttu-id="24edb-124">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-124">Guid</span></span>|  
|<span data-ttu-id="24edb-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-125">DESCRIPTION</span></span>|<span data-ttu-id="24edb-126">String</span><span class="sxs-lookup"><span data-stu-id="24edb-126">String</span></span>|  
|<span data-ttu-id="24edb-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-127">TABLE_PROPID</span></span>|<span data-ttu-id="24edb-128">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-128">Int64</span></span>|  
|<span data-ttu-id="24edb-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-129">DATE_CREATED</span></span>|<span data-ttu-id="24edb-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-130">DateTime</span></span>|  
|<span data-ttu-id="24edb-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-131">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="24edb-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-133">Columns</span></span>  
  
|<span data-ttu-id="24edb-134">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-134">ColumnName</span></span>|<span data-ttu-id="24edb-135">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-136">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-137">String</span><span class="sxs-lookup"><span data-stu-id="24edb-137">String</span></span>|  
|<span data-ttu-id="24edb-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-139">String</span><span class="sxs-lookup"><span data-stu-id="24edb-139">String</span></span>|  
|<span data-ttu-id="24edb-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-140">TABLE_NAME</span></span>|<span data-ttu-id="24edb-141">String</span><span class="sxs-lookup"><span data-stu-id="24edb-141">String</span></span>|  
|<span data-ttu-id="24edb-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-142">COLUMN_NAME</span></span>|<span data-ttu-id="24edb-143">String</span><span class="sxs-lookup"><span data-stu-id="24edb-143">String</span></span>|  
|<span data-ttu-id="24edb-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-144">COLUMN_GUID</span></span>|<span data-ttu-id="24edb-145">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-145">Guid</span></span>|  
|<span data-ttu-id="24edb-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-146">COLUMN_PROPID</span></span>|<span data-ttu-id="24edb-147">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-147">Int64</span></span>|  
|<span data-ttu-id="24edb-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-149">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-149">Int64</span></span>|  
|<span data-ttu-id="24edb-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="24edb-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-151">Boolean</span></span>|  
|<span data-ttu-id="24edb-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="24edb-153">String</span><span class="sxs-lookup"><span data-stu-id="24edb-153">String</span></span>|  
|<span data-ttu-id="24edb-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="24edb-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="24edb-155">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-155">Int64</span></span>|  
|<span data-ttu-id="24edb-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="24edb-156">IS_NULLABLE</span></span>|<span data-ttu-id="24edb-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-157">Boolean</span></span>|  
|<span data-ttu-id="24edb-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-158">DATA_TYPE</span></span>|<span data-ttu-id="24edb-159">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-159">Int32</span></span>|  
|<span data-ttu-id="24edb-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-160">TYPE_GUID</span></span>|<span data-ttu-id="24edb-161">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-161">Guid</span></span>|  
|<span data-ttu-id="24edb-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="24edb-163">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-163">Int64</span></span>|  
|<span data-ttu-id="24edb-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="24edb-165">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-165">Int64</span></span>|  
|<span data-ttu-id="24edb-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="24edb-167">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-167">Int32</span></span>|  
|<span data-ttu-id="24edb-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="24edb-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="24edb-169">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-169">Int16</span></span>|  
|<span data-ttu-id="24edb-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="24edb-171">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-171">Int64</span></span>|  
|<span data-ttu-id="24edb-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="24edb-173">String</span><span class="sxs-lookup"><span data-stu-id="24edb-173">String</span></span>|  
|<span data-ttu-id="24edb-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="24edb-175">String</span><span class="sxs-lookup"><span data-stu-id="24edb-175">String</span></span>|  
|<span data-ttu-id="24edb-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="24edb-177">String</span><span class="sxs-lookup"><span data-stu-id="24edb-177">String</span></span>|  
|<span data-ttu-id="24edb-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="24edb-179">String</span><span class="sxs-lookup"><span data-stu-id="24edb-179">String</span></span>|  
|<span data-ttu-id="24edb-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="24edb-181">String</span><span class="sxs-lookup"><span data-stu-id="24edb-181">String</span></span>|  
|<span data-ttu-id="24edb-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-182">COLLATION_NAME</span></span>|<span data-ttu-id="24edb-183">String</span><span class="sxs-lookup"><span data-stu-id="24edb-183">String</span></span>|  
|<span data-ttu-id="24edb-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="24edb-185">String</span><span class="sxs-lookup"><span data-stu-id="24edb-185">String</span></span>|  
|<span data-ttu-id="24edb-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="24edb-187">String</span><span class="sxs-lookup"><span data-stu-id="24edb-187">String</span></span>|  
|<span data-ttu-id="24edb-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-188">DOMAIN_NAME</span></span>|<span data-ttu-id="24edb-189">String</span><span class="sxs-lookup"><span data-stu-id="24edb-189">String</span></span>|  
|<span data-ttu-id="24edb-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-190">DESCRIPTION</span></span>|<span data-ttu-id="24edb-191">String</span><span class="sxs-lookup"><span data-stu-id="24edb-191">String</span></span>|  
|<span data-ttu-id="24edb-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="24edb-192">COLUMN_LCID</span></span>|<span data-ttu-id="24edb-193">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-193">Int32</span></span>|  
|<span data-ttu-id="24edb-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="24edb-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="24edb-195">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-195">Int32</span></span>|  
|<span data-ttu-id="24edb-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="24edb-196">COLUMN_SORTID</span></span>|<span data-ttu-id="24edb-197">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-197">Int32</span></span>|  
|<span data-ttu-id="24edb-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="24edb-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="24edb-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="24edb-199">Byte[]</span></span>|  
|<span data-ttu-id="24edb-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="24edb-200">IS_COMPUTED</span></span>|<span data-ttu-id="24edb-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="24edb-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="24edb-202">Procedures</span></span>  
  
|<span data-ttu-id="24edb-203">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-203">ColumnName</span></span>|<span data-ttu-id="24edb-204">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="24edb-206">String</span><span class="sxs-lookup"><span data-stu-id="24edb-206">String</span></span>|  
|<span data-ttu-id="24edb-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="24edb-208">String</span><span class="sxs-lookup"><span data-stu-id="24edb-208">String</span></span>|  
|<span data-ttu-id="24edb-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="24edb-210">String</span><span class="sxs-lookup"><span data-stu-id="24edb-210">String</span></span>|  
|<span data-ttu-id="24edb-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="24edb-212">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-212">Int16</span></span>|  
|<span data-ttu-id="24edb-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="24edb-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="24edb-214">String</span><span class="sxs-lookup"><span data-stu-id="24edb-214">String</span></span>|  
|<span data-ttu-id="24edb-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-215">DESCRIPTION</span></span>|<span data-ttu-id="24edb-216">String</span><span class="sxs-lookup"><span data-stu-id="24edb-216">String</span></span>|  
|<span data-ttu-id="24edb-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-217">DATE_CREATED</span></span>|<span data-ttu-id="24edb-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-218">DateTime</span></span>|  
|<span data-ttu-id="24edb-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-219">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="24edb-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="24edb-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="24edb-222">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-222">ColumnName</span></span>|<span data-ttu-id="24edb-223">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="24edb-225">String</span><span class="sxs-lookup"><span data-stu-id="24edb-225">String</span></span>|  
|<span data-ttu-id="24edb-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="24edb-227">String</span><span class="sxs-lookup"><span data-stu-id="24edb-227">String</span></span>|  
|<span data-ttu-id="24edb-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="24edb-229">String</span><span class="sxs-lookup"><span data-stu-id="24edb-229">String</span></span>|  
|<span data-ttu-id="24edb-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-230">PARAMETER_NAME</span></span>|<span data-ttu-id="24edb-231">String</span><span class="sxs-lookup"><span data-stu-id="24edb-231">String</span></span>|  
|<span data-ttu-id="24edb-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-233">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-233">Int32</span></span>|  
|<span data-ttu-id="24edb-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="24edb-235">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-235">Int32</span></span>|  
|<span data-ttu-id="24edb-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="24edb-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-237">Boolean</span></span>|  
|<span data-ttu-id="24edb-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="24edb-239">String</span><span class="sxs-lookup"><span data-stu-id="24edb-239">String</span></span>|  
|<span data-ttu-id="24edb-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="24edb-240">IS_NULLABLE</span></span>|<span data-ttu-id="24edb-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-241">Boolean</span></span>|  
|<span data-ttu-id="24edb-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-242">DATA_TYPE</span></span>|<span data-ttu-id="24edb-243">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-243">Int32</span></span>|  
|<span data-ttu-id="24edb-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="24edb-245">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-245">Int64</span></span>|  
|<span data-ttu-id="24edb-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="24edb-247">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-247">Int64</span></span>|  
|<span data-ttu-id="24edb-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="24edb-249">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-249">Int32</span></span>|  
|<span data-ttu-id="24edb-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="24edb-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="24edb-251">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-251">Int16</span></span>|  
|<span data-ttu-id="24edb-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-252">DESCRIPTION</span></span>|<span data-ttu-id="24edb-253">String</span><span class="sxs-lookup"><span data-stu-id="24edb-253">String</span></span>|  
|<span data-ttu-id="24edb-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-254">TYPE_NAME</span></span>|<span data-ttu-id="24edb-255">String</span><span class="sxs-lookup"><span data-stu-id="24edb-255">String</span></span>|  
|<span data-ttu-id="24edb-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="24edb-257">String</span><span class="sxs-lookup"><span data-stu-id="24edb-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="24edb-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="24edb-258">Catalog</span></span>  
  
|<span data-ttu-id="24edb-259">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-259">ColumnName</span></span>|<span data-ttu-id="24edb-260">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-261">CATALOG_NAME</span></span>|<span data-ttu-id="24edb-262">String</span><span class="sxs-lookup"><span data-stu-id="24edb-262">String</span></span>|  
|<span data-ttu-id="24edb-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-263">DESCRIPTION</span></span>|<span data-ttu-id="24edb-264">String</span><span class="sxs-lookup"><span data-stu-id="24edb-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="24edb-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="24edb-265">Indexes</span></span>  
  
|<span data-ttu-id="24edb-266">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-266">ColumnName</span></span>|<span data-ttu-id="24edb-267">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-268">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-269">String</span><span class="sxs-lookup"><span data-stu-id="24edb-269">String</span></span>|  
|<span data-ttu-id="24edb-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-271">String</span><span class="sxs-lookup"><span data-stu-id="24edb-271">String</span></span>|  
|<span data-ttu-id="24edb-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-272">TABLE_NAME</span></span>|<span data-ttu-id="24edb-273">String</span><span class="sxs-lookup"><span data-stu-id="24edb-273">String</span></span>|  
|<span data-ttu-id="24edb-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-274">INDEX_CATALOG</span></span>|<span data-ttu-id="24edb-275">String</span><span class="sxs-lookup"><span data-stu-id="24edb-275">String</span></span>|  
|<span data-ttu-id="24edb-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="24edb-277">String</span><span class="sxs-lookup"><span data-stu-id="24edb-277">String</span></span>|  
|<span data-ttu-id="24edb-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-278">INDEX_NAME</span></span>|<span data-ttu-id="24edb-279">String</span><span class="sxs-lookup"><span data-stu-id="24edb-279">String</span></span>|  
|<span data-ttu-id="24edb-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="24edb-280">PRIMARY_KEY</span></span>|<span data-ttu-id="24edb-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-281">Boolean</span></span>|  
|<span data-ttu-id="24edb-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="24edb-282">UNIQUE</span></span>|<span data-ttu-id="24edb-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-283">Boolean</span></span>|  
|<span data-ttu-id="24edb-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="24edb-284">CLUSTERED</span></span>|<span data-ttu-id="24edb-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-285">Boolean</span></span>|  
|<span data-ttu-id="24edb-286">TYP</span><span class="sxs-lookup"><span data-stu-id="24edb-286">TYPE</span></span>|<span data-ttu-id="24edb-287">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-287">Int32</span></span>|  
|<span data-ttu-id="24edb-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="24edb-288">FILL_FACTOR</span></span>|<span data-ttu-id="24edb-289">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-289">Int32</span></span>|  
|<span data-ttu-id="24edb-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="24edb-290">INITIAL_SIZE</span></span>|<span data-ttu-id="24edb-291">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-291">Int32</span></span>|  
|<span data-ttu-id="24edb-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="24edb-292">NULLS</span></span>|<span data-ttu-id="24edb-293">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-293">Int32</span></span>|  
|<span data-ttu-id="24edb-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="24edb-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="24edb-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-295">Boolean</span></span>|  
|<span data-ttu-id="24edb-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="24edb-296">AUTO_UPDATE</span></span>|<span data-ttu-id="24edb-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-297">Boolean</span></span>|  
|<span data-ttu-id="24edb-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="24edb-298">NULL_COLLATION</span></span>|<span data-ttu-id="24edb-299">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-299">Int32</span></span>|  
|<span data-ttu-id="24edb-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-301">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-301">Int64</span></span>|  
|<span data-ttu-id="24edb-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-302">COLUMN_NAME</span></span>|<span data-ttu-id="24edb-303">String</span><span class="sxs-lookup"><span data-stu-id="24edb-303">String</span></span>|  
|<span data-ttu-id="24edb-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-304">COLUMN_GUID</span></span>|<span data-ttu-id="24edb-305">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-305">Guid</span></span>|  
|<span data-ttu-id="24edb-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-306">COLUMN_PROPID</span></span>|<span data-ttu-id="24edb-307">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-307">Int64</span></span>|  
|<span data-ttu-id="24edb-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="24edb-308">COLLATION</span></span>|<span data-ttu-id="24edb-309">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-309">Int16</span></span>|  
|<span data-ttu-id="24edb-310">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="24edb-310">CARDINALITY</span></span>|<span data-ttu-id="24edb-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="24edb-311">Decimal</span></span>|  
|<span data-ttu-id="24edb-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="24edb-312">PAGES</span></span>|<span data-ttu-id="24edb-313">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-313">Int32</span></span>|  
|<span data-ttu-id="24edb-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="24edb-314">FILTER_CONDITION</span></span>|<span data-ttu-id="24edb-315">String</span><span class="sxs-lookup"><span data-stu-id="24edb-315">String</span></span>|  
|<span data-ttu-id="24edb-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="24edb-316">INTEGRATED</span></span>|<span data-ttu-id="24edb-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="24edb-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="24edb-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="24edb-319">Oracle OLE DB ovladač Microsoft podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="24edb-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="24edb-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="24edb-320">Tables</span></span>  
  
- <span data-ttu-id="24edb-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-321">Columns</span></span>  
  
- <span data-ttu-id="24edb-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="24edb-322">Procedures</span></span>  
  
- <span data-ttu-id="24edb-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="24edb-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="24edb-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="24edb-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="24edb-325">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="24edb-325">Views</span></span>  
  
- <span data-ttu-id="24edb-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="24edb-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="24edb-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="24edb-327">Tables</span></span>  
  
|<span data-ttu-id="24edb-328">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-328">ColumnName</span></span>|<span data-ttu-id="24edb-329">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-330">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-331">String</span><span class="sxs-lookup"><span data-stu-id="24edb-331">String</span></span>|  
|<span data-ttu-id="24edb-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-333">String</span><span class="sxs-lookup"><span data-stu-id="24edb-333">String</span></span>|  
|<span data-ttu-id="24edb-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-334">TABLE_NAME</span></span>|<span data-ttu-id="24edb-335">String</span><span class="sxs-lookup"><span data-stu-id="24edb-335">String</span></span>|  
|<span data-ttu-id="24edb-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-336">TABLE_TYPE</span></span>|<span data-ttu-id="24edb-337">String</span><span class="sxs-lookup"><span data-stu-id="24edb-337">String</span></span>|  
|<span data-ttu-id="24edb-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-338">TABLE_GUID</span></span>|<span data-ttu-id="24edb-339">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-339">Guid</span></span>|  
|<span data-ttu-id="24edb-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-340">DESCRIPTION</span></span>|<span data-ttu-id="24edb-341">String</span><span class="sxs-lookup"><span data-stu-id="24edb-341">String</span></span>|  
|<span data-ttu-id="24edb-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-342">TABLE_PROPID</span></span>|<span data-ttu-id="24edb-343">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-343">Int64</span></span>|  
|<span data-ttu-id="24edb-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-344">DATE_CREATED</span></span>|<span data-ttu-id="24edb-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-345">DateTime</span></span>|  
|<span data-ttu-id="24edb-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-346">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="24edb-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-348">Columns</span></span>  
  
|<span data-ttu-id="24edb-349">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-349">ColumnName</span></span>|<span data-ttu-id="24edb-350">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-351">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-352">String</span><span class="sxs-lookup"><span data-stu-id="24edb-352">String</span></span>|  
|<span data-ttu-id="24edb-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-354">String</span><span class="sxs-lookup"><span data-stu-id="24edb-354">String</span></span>|  
|<span data-ttu-id="24edb-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-355">TABLE_NAME</span></span>|<span data-ttu-id="24edb-356">String</span><span class="sxs-lookup"><span data-stu-id="24edb-356">String</span></span>|  
|<span data-ttu-id="24edb-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-357">COLUMN_NAME</span></span>|<span data-ttu-id="24edb-358">String</span><span class="sxs-lookup"><span data-stu-id="24edb-358">String</span></span>|  
|<span data-ttu-id="24edb-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-359">COLUMN_GUID</span></span>|<span data-ttu-id="24edb-360">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-360">Guid</span></span>|  
|<span data-ttu-id="24edb-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-361">COLUMN_PROPID</span></span>|<span data-ttu-id="24edb-362">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-362">Int64</span></span>|  
|<span data-ttu-id="24edb-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-364">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-364">Int64</span></span>|  
|<span data-ttu-id="24edb-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="24edb-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-366">Boolean</span></span>|  
|<span data-ttu-id="24edb-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="24edb-368">String</span><span class="sxs-lookup"><span data-stu-id="24edb-368">String</span></span>|  
|<span data-ttu-id="24edb-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="24edb-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="24edb-370">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-370">Int64</span></span>|  
|<span data-ttu-id="24edb-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="24edb-371">IS_NULLABLE</span></span>|<span data-ttu-id="24edb-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-372">Boolean</span></span>|  
|<span data-ttu-id="24edb-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-373">DATA_TYPE</span></span>|<span data-ttu-id="24edb-374">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-374">Int32</span></span>|  
|<span data-ttu-id="24edb-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-375">TYPE_GUID</span></span>|<span data-ttu-id="24edb-376">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-376">Guid</span></span>|  
|<span data-ttu-id="24edb-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="24edb-378">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-378">Int64</span></span>|  
|<span data-ttu-id="24edb-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="24edb-380">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-380">Int64</span></span>|  
|<span data-ttu-id="24edb-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="24edb-382">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-382">Int32</span></span>|  
|<span data-ttu-id="24edb-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="24edb-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="24edb-384">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-384">Int16</span></span>|  
|<span data-ttu-id="24edb-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="24edb-386">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-386">Int64</span></span>|  
|<span data-ttu-id="24edb-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="24edb-388">String</span><span class="sxs-lookup"><span data-stu-id="24edb-388">String</span></span>|  
|<span data-ttu-id="24edb-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="24edb-390">String</span><span class="sxs-lookup"><span data-stu-id="24edb-390">String</span></span>|  
|<span data-ttu-id="24edb-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="24edb-392">String</span><span class="sxs-lookup"><span data-stu-id="24edb-392">String</span></span>|  
|<span data-ttu-id="24edb-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="24edb-394">String</span><span class="sxs-lookup"><span data-stu-id="24edb-394">String</span></span>|  
|<span data-ttu-id="24edb-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="24edb-396">String</span><span class="sxs-lookup"><span data-stu-id="24edb-396">String</span></span>|  
|<span data-ttu-id="24edb-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-397">COLLATION_NAME</span></span>|<span data-ttu-id="24edb-398">String</span><span class="sxs-lookup"><span data-stu-id="24edb-398">String</span></span>|  
|<span data-ttu-id="24edb-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="24edb-400">String</span><span class="sxs-lookup"><span data-stu-id="24edb-400">String</span></span>|  
|<span data-ttu-id="24edb-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="24edb-402">String</span><span class="sxs-lookup"><span data-stu-id="24edb-402">String</span></span>|  
|<span data-ttu-id="24edb-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-403">DOMAIN_NAME</span></span>|<span data-ttu-id="24edb-404">String</span><span class="sxs-lookup"><span data-stu-id="24edb-404">String</span></span>|  
|<span data-ttu-id="24edb-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-405">DESCRIPTION</span></span>|<span data-ttu-id="24edb-406">String</span><span class="sxs-lookup"><span data-stu-id="24edb-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="24edb-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="24edb-407">Procedures</span></span>  
  
|<span data-ttu-id="24edb-408">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-408">ColumnName</span></span>|<span data-ttu-id="24edb-409">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="24edb-411">String</span><span class="sxs-lookup"><span data-stu-id="24edb-411">String</span></span>|  
|<span data-ttu-id="24edb-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="24edb-413">String</span><span class="sxs-lookup"><span data-stu-id="24edb-413">String</span></span>|  
|<span data-ttu-id="24edb-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="24edb-415">String</span><span class="sxs-lookup"><span data-stu-id="24edb-415">String</span></span>|  
|<span data-ttu-id="24edb-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="24edb-417">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-417">Int16</span></span>|  
|<span data-ttu-id="24edb-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="24edb-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="24edb-419">String</span><span class="sxs-lookup"><span data-stu-id="24edb-419">String</span></span>|  
|<span data-ttu-id="24edb-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-420">DESCRIPTION</span></span>|<span data-ttu-id="24edb-421">String</span><span class="sxs-lookup"><span data-stu-id="24edb-421">String</span></span>|  
|<span data-ttu-id="24edb-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-422">DATE_CREATED</span></span>|<span data-ttu-id="24edb-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-423">DateTime</span></span>|  
|<span data-ttu-id="24edb-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-424">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="24edb-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="24edb-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="24edb-427">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-427">ColumnName</span></span>|<span data-ttu-id="24edb-428">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="24edb-430">String</span><span class="sxs-lookup"><span data-stu-id="24edb-430">String</span></span>|  
|<span data-ttu-id="24edb-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="24edb-432">String</span><span class="sxs-lookup"><span data-stu-id="24edb-432">String</span></span>|  
|<span data-ttu-id="24edb-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="24edb-434">String</span><span class="sxs-lookup"><span data-stu-id="24edb-434">String</span></span>|  
|<span data-ttu-id="24edb-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-435">COLUMN_NAME</span></span>|<span data-ttu-id="24edb-436">String</span><span class="sxs-lookup"><span data-stu-id="24edb-436">String</span></span>|  
|<span data-ttu-id="24edb-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-437">COLUMN_GUID</span></span>|<span data-ttu-id="24edb-438">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-438">Guid</span></span>|  
|<span data-ttu-id="24edb-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-439">COLUMN_PROPID</span></span>|<span data-ttu-id="24edb-440">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-440">Int64</span></span>|  
|<span data-ttu-id="24edb-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="24edb-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="24edb-442">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-442">Int64</span></span>|  
|<span data-ttu-id="24edb-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-444">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-444">Int64</span></span>|  
|<span data-ttu-id="24edb-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="24edb-445">IS_NULLABLE</span></span>|<span data-ttu-id="24edb-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-446">Boolean</span></span>|  
|<span data-ttu-id="24edb-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-447">DATA_TYPE</span></span>|<span data-ttu-id="24edb-448">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-448">Int32</span></span>|  
|<span data-ttu-id="24edb-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-449">TYPE_GUID</span></span>|<span data-ttu-id="24edb-450">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-450">Guid</span></span>|  
|<span data-ttu-id="24edb-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="24edb-452">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-452">Int64</span></span>|  
|<span data-ttu-id="24edb-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="24edb-454">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-454">Int64</span></span>|  
|<span data-ttu-id="24edb-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="24edb-456">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-456">Int32</span></span>|  
|<span data-ttu-id="24edb-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="24edb-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="24edb-458">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-458">Int16</span></span>|  
|<span data-ttu-id="24edb-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-459">DESCRIPTION</span></span>|<span data-ttu-id="24edb-460">String</span><span class="sxs-lookup"><span data-stu-id="24edb-460">String</span></span>|  
|<span data-ttu-id="24edb-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="24edb-461">OVERLOAD</span></span>|<span data-ttu-id="24edb-462">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="24edb-463">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="24edb-463">Views</span></span>  
  
|<span data-ttu-id="24edb-464">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-464">ColumnName</span></span>|<span data-ttu-id="24edb-465">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-466">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-467">String</span><span class="sxs-lookup"><span data-stu-id="24edb-467">String</span></span>|  
|<span data-ttu-id="24edb-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-469">String</span><span class="sxs-lookup"><span data-stu-id="24edb-469">String</span></span>|  
|<span data-ttu-id="24edb-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-470">TABLE_NAME</span></span>|<span data-ttu-id="24edb-471">String</span><span class="sxs-lookup"><span data-stu-id="24edb-471">String</span></span>|  
|<span data-ttu-id="24edb-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="24edb-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="24edb-473">String</span><span class="sxs-lookup"><span data-stu-id="24edb-473">String</span></span>|  
|<span data-ttu-id="24edb-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="24edb-474">CHECK_OPTION</span></span>|<span data-ttu-id="24edb-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-475">Boolean</span></span>|  
|<span data-ttu-id="24edb-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="24edb-476">IS_UPDATABLE</span></span>|<span data-ttu-id="24edb-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-477">Boolean</span></span>|  
|<span data-ttu-id="24edb-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-478">DESCRIPTION</span></span>|<span data-ttu-id="24edb-479">String</span><span class="sxs-lookup"><span data-stu-id="24edb-479">String</span></span>|  
|<span data-ttu-id="24edb-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-480">DATE_CREATED</span></span>|<span data-ttu-id="24edb-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-481">DateTime</span></span>|  
|<span data-ttu-id="24edb-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-482">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="24edb-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="24edb-484">Indexes</span></span>  
  
|<span data-ttu-id="24edb-485">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-485">ColumnName</span></span>|<span data-ttu-id="24edb-486">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-487">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-488">String</span><span class="sxs-lookup"><span data-stu-id="24edb-488">String</span></span>|  
|<span data-ttu-id="24edb-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-490">String</span><span class="sxs-lookup"><span data-stu-id="24edb-490">String</span></span>|  
|<span data-ttu-id="24edb-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-491">TABLE_NAME</span></span>|<span data-ttu-id="24edb-492">String</span><span class="sxs-lookup"><span data-stu-id="24edb-492">String</span></span>|  
|<span data-ttu-id="24edb-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-493">INDEX_CATALOG</span></span>|<span data-ttu-id="24edb-494">String</span><span class="sxs-lookup"><span data-stu-id="24edb-494">String</span></span>|  
|<span data-ttu-id="24edb-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="24edb-496">String</span><span class="sxs-lookup"><span data-stu-id="24edb-496">String</span></span>|  
|<span data-ttu-id="24edb-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-497">INDEX_NAME</span></span>|<span data-ttu-id="24edb-498">String</span><span class="sxs-lookup"><span data-stu-id="24edb-498">String</span></span>|  
|<span data-ttu-id="24edb-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="24edb-499">PRIMARY_KEY</span></span>|<span data-ttu-id="24edb-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-500">Boolean</span></span>|  
|<span data-ttu-id="24edb-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="24edb-501">UNIQUE</span></span>|<span data-ttu-id="24edb-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-502">Boolean</span></span>|  
|<span data-ttu-id="24edb-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="24edb-503">CLUSTERED</span></span>|<span data-ttu-id="24edb-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-504">Boolean</span></span>|  
|<span data-ttu-id="24edb-505">TYP</span><span class="sxs-lookup"><span data-stu-id="24edb-505">TYPE</span></span>|<span data-ttu-id="24edb-506">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-506">Int32</span></span>|  
|<span data-ttu-id="24edb-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="24edb-507">FILL_FACTOR</span></span>|<span data-ttu-id="24edb-508">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-508">Int32</span></span>|  
|<span data-ttu-id="24edb-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="24edb-509">INITIAL_SIZE</span></span>|<span data-ttu-id="24edb-510">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-510">Int32</span></span>|  
|<span data-ttu-id="24edb-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="24edb-511">NULLS</span></span>|<span data-ttu-id="24edb-512">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-512">Int32</span></span>|  
|<span data-ttu-id="24edb-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="24edb-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="24edb-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-514">Boolean</span></span>|  
|<span data-ttu-id="24edb-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="24edb-515">AUTO_UPDATE</span></span>|<span data-ttu-id="24edb-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-516">Boolean</span></span>|  
|<span data-ttu-id="24edb-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="24edb-517">NULL_COLLATION</span></span>|<span data-ttu-id="24edb-518">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-518">Int32</span></span>|  
|<span data-ttu-id="24edb-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-520">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-520">Int64</span></span>|  
|<span data-ttu-id="24edb-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-521">COLUMN_NAME</span></span>|<span data-ttu-id="24edb-522">String</span><span class="sxs-lookup"><span data-stu-id="24edb-522">String</span></span>|  
|<span data-ttu-id="24edb-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-523">COLUMN_GUID</span></span>|<span data-ttu-id="24edb-524">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-524">Guid</span></span>|  
|<span data-ttu-id="24edb-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-525">COLUMN_PROPID</span></span>|<span data-ttu-id="24edb-526">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-526">Int64</span></span>|  
|<span data-ttu-id="24edb-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="24edb-527">COLLATION</span></span>|<span data-ttu-id="24edb-528">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-528">Int16</span></span>|  
|<span data-ttu-id="24edb-529">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="24edb-529">CARDINALITY</span></span>|<span data-ttu-id="24edb-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="24edb-530">Decimal</span></span>|  
|<span data-ttu-id="24edb-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="24edb-531">PAGES</span></span>|<span data-ttu-id="24edb-532">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-532">Int32</span></span>|  
|<span data-ttu-id="24edb-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="24edb-533">FILTER_CONDITION</span></span>|<span data-ttu-id="24edb-534">String</span><span class="sxs-lookup"><span data-stu-id="24edb-534">String</span></span>|  
|<span data-ttu-id="24edb-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="24edb-535">INTEGRATED</span></span>|<span data-ttu-id="24edb-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="24edb-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="24edb-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="24edb-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="24edb-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="24edb-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="24edb-539">Tables</span></span>  
  
- <span data-ttu-id="24edb-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-540">Columns</span></span>  
  
- <span data-ttu-id="24edb-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="24edb-541">Procedures</span></span>  
  
- <span data-ttu-id="24edb-542">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="24edb-542">Views</span></span>  
  
- <span data-ttu-id="24edb-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="24edb-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="24edb-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="24edb-544">Tables</span></span>  
  
|<span data-ttu-id="24edb-545">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-545">ColumnName</span></span>|<span data-ttu-id="24edb-546">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-547">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-548">String</span><span class="sxs-lookup"><span data-stu-id="24edb-548">String</span></span>|  
|<span data-ttu-id="24edb-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-550">String</span><span class="sxs-lookup"><span data-stu-id="24edb-550">String</span></span>|  
|<span data-ttu-id="24edb-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-551">TABLE_NAME</span></span>|<span data-ttu-id="24edb-552">String</span><span class="sxs-lookup"><span data-stu-id="24edb-552">String</span></span>|  
|<span data-ttu-id="24edb-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-553">TABLE_TYPE</span></span>|<span data-ttu-id="24edb-554">String</span><span class="sxs-lookup"><span data-stu-id="24edb-554">String</span></span>|  
|<span data-ttu-id="24edb-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-555">TABLE_GUID</span></span>|<span data-ttu-id="24edb-556">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-556">Guid</span></span>|  
|<span data-ttu-id="24edb-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-557">DESCRIPTION</span></span>|<span data-ttu-id="24edb-558">String</span><span class="sxs-lookup"><span data-stu-id="24edb-558">String</span></span>|  
|<span data-ttu-id="24edb-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-559">TABLE_PROPID</span></span>|<span data-ttu-id="24edb-560">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-560">Int64</span></span>|  
|<span data-ttu-id="24edb-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-561">DATE_CREATED</span></span>|<span data-ttu-id="24edb-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-562">DateTime</span></span>|  
|<span data-ttu-id="24edb-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-563">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="24edb-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-565">Columns</span></span>  
  
|<span data-ttu-id="24edb-566">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-566">ColumnName</span></span>|<span data-ttu-id="24edb-567">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-568">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-569">String</span><span class="sxs-lookup"><span data-stu-id="24edb-569">String</span></span>|  
|<span data-ttu-id="24edb-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-571">String</span><span class="sxs-lookup"><span data-stu-id="24edb-571">String</span></span>|  
|<span data-ttu-id="24edb-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-572">TABLE_NAME</span></span>|<span data-ttu-id="24edb-573">String</span><span class="sxs-lookup"><span data-stu-id="24edb-573">String</span></span>|  
|<span data-ttu-id="24edb-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-574">COLUMN_NAME</span></span>|<span data-ttu-id="24edb-575">String</span><span class="sxs-lookup"><span data-stu-id="24edb-575">String</span></span>|  
|<span data-ttu-id="24edb-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-576">COLUMN_GUID</span></span>|<span data-ttu-id="24edb-577">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-577">Guid</span></span>|  
|<span data-ttu-id="24edb-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-578">COLUMN_PROPID</span></span>|<span data-ttu-id="24edb-579">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-579">Int64</span></span>|  
|<span data-ttu-id="24edb-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-581">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-581">Int64</span></span>|  
|<span data-ttu-id="24edb-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="24edb-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-583">Boolean</span></span>|  
|<span data-ttu-id="24edb-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="24edb-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="24edb-585">String</span><span class="sxs-lookup"><span data-stu-id="24edb-585">String</span></span>|  
|<span data-ttu-id="24edb-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="24edb-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="24edb-587">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-587">Int64</span></span>|  
|<span data-ttu-id="24edb-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="24edb-588">IS_NULLABLE</span></span>|<span data-ttu-id="24edb-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-589">Boolean</span></span>|  
|<span data-ttu-id="24edb-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-590">DATA_TYPE</span></span>|<span data-ttu-id="24edb-591">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-591">Int32</span></span>|  
|<span data-ttu-id="24edb-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-592">TYPE_GUID</span></span>|<span data-ttu-id="24edb-593">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-593">Guid</span></span>|  
|<span data-ttu-id="24edb-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="24edb-595">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-595">Int64</span></span>|  
|<span data-ttu-id="24edb-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="24edb-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="24edb-597">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-597">Int64</span></span>|  
|<span data-ttu-id="24edb-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="24edb-599">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-599">Int32</span></span>|  
|<span data-ttu-id="24edb-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="24edb-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="24edb-601">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-601">Int16</span></span>|  
|<span data-ttu-id="24edb-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="24edb-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="24edb-603">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-603">Int64</span></span>|  
|<span data-ttu-id="24edb-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="24edb-605">String</span><span class="sxs-lookup"><span data-stu-id="24edb-605">String</span></span>|  
|<span data-ttu-id="24edb-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="24edb-607">String</span><span class="sxs-lookup"><span data-stu-id="24edb-607">String</span></span>|  
|<span data-ttu-id="24edb-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="24edb-609">String</span><span class="sxs-lookup"><span data-stu-id="24edb-609">String</span></span>|  
|<span data-ttu-id="24edb-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="24edb-611">String</span><span class="sxs-lookup"><span data-stu-id="24edb-611">String</span></span>|  
|<span data-ttu-id="24edb-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="24edb-613">String</span><span class="sxs-lookup"><span data-stu-id="24edb-613">String</span></span>|  
|<span data-ttu-id="24edb-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-614">COLLATION_NAME</span></span>|<span data-ttu-id="24edb-615">String</span><span class="sxs-lookup"><span data-stu-id="24edb-615">String</span></span>|  
|<span data-ttu-id="24edb-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="24edb-617">String</span><span class="sxs-lookup"><span data-stu-id="24edb-617">String</span></span>|  
|<span data-ttu-id="24edb-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="24edb-619">String</span><span class="sxs-lookup"><span data-stu-id="24edb-619">String</span></span>|  
|<span data-ttu-id="24edb-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-620">DOMAIN_NAME</span></span>|<span data-ttu-id="24edb-621">String</span><span class="sxs-lookup"><span data-stu-id="24edb-621">String</span></span>|  
|<span data-ttu-id="24edb-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-622">DESCRIPTION</span></span>|<span data-ttu-id="24edb-623">String</span><span class="sxs-lookup"><span data-stu-id="24edb-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="24edb-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="24edb-624">Procedures</span></span>  
  
|<span data-ttu-id="24edb-625">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-625">ColumnName</span></span>|<span data-ttu-id="24edb-626">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="24edb-628">String</span><span class="sxs-lookup"><span data-stu-id="24edb-628">String</span></span>|  
|<span data-ttu-id="24edb-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="24edb-630">String</span><span class="sxs-lookup"><span data-stu-id="24edb-630">String</span></span>|  
|<span data-ttu-id="24edb-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="24edb-632">String</span><span class="sxs-lookup"><span data-stu-id="24edb-632">String</span></span>|  
|<span data-ttu-id="24edb-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="24edb-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="24edb-634">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-634">Int16</span></span>|  
|<span data-ttu-id="24edb-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="24edb-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="24edb-636">String</span><span class="sxs-lookup"><span data-stu-id="24edb-636">String</span></span>|  
|<span data-ttu-id="24edb-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-637">DESCRIPTION</span></span>|<span data-ttu-id="24edb-638">String</span><span class="sxs-lookup"><span data-stu-id="24edb-638">String</span></span>|  
|<span data-ttu-id="24edb-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-639">DATE_CREATED</span></span>|<span data-ttu-id="24edb-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-640">DateTime</span></span>|  
|<span data-ttu-id="24edb-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-641">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="24edb-643">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="24edb-643">Views</span></span>  
  
|<span data-ttu-id="24edb-644">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-644">ColumnName</span></span>|<span data-ttu-id="24edb-645">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-646">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-647">String</span><span class="sxs-lookup"><span data-stu-id="24edb-647">String</span></span>|  
|<span data-ttu-id="24edb-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-649">String</span><span class="sxs-lookup"><span data-stu-id="24edb-649">String</span></span>|  
|<span data-ttu-id="24edb-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-650">TABLE_NAME</span></span>|<span data-ttu-id="24edb-651">String</span><span class="sxs-lookup"><span data-stu-id="24edb-651">String</span></span>|  
|<span data-ttu-id="24edb-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="24edb-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="24edb-653">String</span><span class="sxs-lookup"><span data-stu-id="24edb-653">String</span></span>|  
|<span data-ttu-id="24edb-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="24edb-654">CHECK_OPTION</span></span>|<span data-ttu-id="24edb-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-655">Boolean</span></span>|  
|<span data-ttu-id="24edb-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="24edb-656">IS_UPDATABLE</span></span>|<span data-ttu-id="24edb-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-657">Boolean</span></span>|  
|<span data-ttu-id="24edb-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="24edb-658">DESCRIPTION</span></span>|<span data-ttu-id="24edb-659">String</span><span class="sxs-lookup"><span data-stu-id="24edb-659">String</span></span>|  
|<span data-ttu-id="24edb-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="24edb-660">DATE_CREATED</span></span>|<span data-ttu-id="24edb-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-661">DateTime</span></span>|  
|<span data-ttu-id="24edb-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="24edb-662">DATE_MODIFIED</span></span>|<span data-ttu-id="24edb-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="24edb-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="24edb-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="24edb-664">Indexes</span></span>  
  
|<span data-ttu-id="24edb-665">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="24edb-665">ColumnName</span></span>|<span data-ttu-id="24edb-666">DataType</span><span class="sxs-lookup"><span data-stu-id="24edb-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="24edb-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-667">TABLE_CATALOG</span></span>|<span data-ttu-id="24edb-668">String</span><span class="sxs-lookup"><span data-stu-id="24edb-668">String</span></span>|  
|<span data-ttu-id="24edb-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="24edb-670">String</span><span class="sxs-lookup"><span data-stu-id="24edb-670">String</span></span>|  
|<span data-ttu-id="24edb-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-671">TABLE_NAME</span></span>|<span data-ttu-id="24edb-672">String</span><span class="sxs-lookup"><span data-stu-id="24edb-672">String</span></span>|  
|<span data-ttu-id="24edb-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="24edb-673">INDEX_CATALOG</span></span>|<span data-ttu-id="24edb-674">String</span><span class="sxs-lookup"><span data-stu-id="24edb-674">String</span></span>|  
|<span data-ttu-id="24edb-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="24edb-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="24edb-676">String</span><span class="sxs-lookup"><span data-stu-id="24edb-676">String</span></span>|  
|<span data-ttu-id="24edb-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-677">INDEX_NAME</span></span>|<span data-ttu-id="24edb-678">String</span><span class="sxs-lookup"><span data-stu-id="24edb-678">String</span></span>|  
|<span data-ttu-id="24edb-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="24edb-679">PRIMARY_KEY</span></span>|<span data-ttu-id="24edb-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-680">Boolean</span></span>|  
|<span data-ttu-id="24edb-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="24edb-681">UNIQUE</span></span>|<span data-ttu-id="24edb-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-682">Boolean</span></span>|  
|<span data-ttu-id="24edb-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="24edb-683">CLUSTERED</span></span>|<span data-ttu-id="24edb-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-684">Boolean</span></span>|  
|<span data-ttu-id="24edb-685">TYP</span><span class="sxs-lookup"><span data-stu-id="24edb-685">TYPE</span></span>|<span data-ttu-id="24edb-686">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-686">Int32</span></span>|  
|<span data-ttu-id="24edb-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="24edb-687">FILL_FACTOR</span></span>|<span data-ttu-id="24edb-688">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-688">Int32</span></span>|  
|<span data-ttu-id="24edb-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="24edb-689">INITIAL_SIZE</span></span>|<span data-ttu-id="24edb-690">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-690">Int32</span></span>|  
|<span data-ttu-id="24edb-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="24edb-691">NULLS</span></span>|<span data-ttu-id="24edb-692">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-692">Int32</span></span>|  
|<span data-ttu-id="24edb-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="24edb-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="24edb-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-694">Boolean</span></span>|  
|<span data-ttu-id="24edb-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="24edb-695">AUTO_UPDATE</span></span>|<span data-ttu-id="24edb-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-696">Boolean</span></span>|  
|<span data-ttu-id="24edb-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="24edb-697">NULL_COLLATION</span></span>|<span data-ttu-id="24edb-698">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-698">Int32</span></span>|  
|<span data-ttu-id="24edb-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="24edb-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="24edb-700">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-700">Int64</span></span>|  
|<span data-ttu-id="24edb-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="24edb-701">COLUMN_NAME</span></span>|<span data-ttu-id="24edb-702">String</span><span class="sxs-lookup"><span data-stu-id="24edb-702">String</span></span>|  
|<span data-ttu-id="24edb-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="24edb-703">COLUMN_GUID</span></span>|<span data-ttu-id="24edb-704">Guid</span><span class="sxs-lookup"><span data-stu-id="24edb-704">Guid</span></span>|  
|<span data-ttu-id="24edb-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="24edb-705">COLUMN_PROPID</span></span>|<span data-ttu-id="24edb-706">Int64</span><span class="sxs-lookup"><span data-stu-id="24edb-706">Int64</span></span>|  
|<span data-ttu-id="24edb-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="24edb-707">COLLATION</span></span>|<span data-ttu-id="24edb-708">Int16</span><span class="sxs-lookup"><span data-stu-id="24edb-708">Int16</span></span>|  
|<span data-ttu-id="24edb-709">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="24edb-709">CARDINALITY</span></span>|<span data-ttu-id="24edb-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="24edb-710">Decimal</span></span>|  
|<span data-ttu-id="24edb-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="24edb-711">PAGES</span></span>|<span data-ttu-id="24edb-712">Int32</span><span class="sxs-lookup"><span data-stu-id="24edb-712">Int32</span></span>|  
|<span data-ttu-id="24edb-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="24edb-713">FILTER_CONDITION</span></span>|<span data-ttu-id="24edb-714">String</span><span class="sxs-lookup"><span data-stu-id="24edb-714">String</span></span>|  
|<span data-ttu-id="24edb-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="24edb-715">INTEGRATED</span></span>|<span data-ttu-id="24edb-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="24edb-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24edb-717">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24edb-717">See also</span></span>

- [<span data-ttu-id="24edb-718">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="24edb-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
